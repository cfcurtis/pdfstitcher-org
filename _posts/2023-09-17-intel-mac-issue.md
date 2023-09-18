---
title: "Issue with Intel macOS"
last_modified_at: 2023-09-17
excerpt: "If you have an Intel mac running macOS 13 (Ventura), there is an issue loading encrypted PDFs."
toc: true
release: 'v0.9.1'
---

## The problem
After updating PDFStitcher to handle large canvas files, I went through my usual process of bundling the Python code for various operating systems using PyInstaller on GitHub action runners. This time, I started getting reports from users with the following message:

```
Runtime error: unable to load OpenSSL legacy provider
```

After some investigation, I believe that this is only a problem under the following conditions:

* macOS 13 (Ventura)
* Intel processor (not Apple Silicon)
* Encrypted PDF (I'm not sure if the exact encryption method matters)

## The workaround
For now, there are a couple of potential band-aid solutions. The easiest is to remove the PDF encryption through a PDF "unlock" tool, at which point PDFStitcher will behave normally (I don't like to encourage such things, but I also know that sewists are by and large a respectful bunch and just trying to adapt patterns for their personal use).

Another workaround is to install Python and then install PDFStitcher through pip via the command:

```bash
pip3 install pdfstitcher
```

but you lose the fancy .app packaging and need to run it from the command line by typing `pdfstitcher`.

## The long term solution
Unfortunately, I do not have an Intel mac, which makes finding the root cause of the problem rather tricky. GitHub *does* have a macOS 13 action runner, and I was able to create a minimal example and replicate the problem [here](https://github.com/cfcurtis/pdfstitcher/actions/runs/5868374229/job/15911100861#step:4:10), but a subsequent run of the same workflow did not repeat it. My guess is that not all runners are identical, and something about how QPDF (the PDF library that I use through the Python wrapper Pikepdf) is built on macOS-11 is not compatible with the OpenSSL library on macOS-13. Or maybe there's a problem with how I'm using PyInstaller, or something else entirely - unfortunately without a consistent way to replicate the problem, I'm just guessing.

## My request for help!
If you have encountered this problem, have a bit of programming experience, and are willing to help me figure out what's going on, please [comment on this issue](https://github.com/cfcurtis/pdfstitcher/issues/195) or send me an [email](mailto:ccurtis@mtroyal.ca).