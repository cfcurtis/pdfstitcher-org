---
permalink: /docs/download
title: "Download"
last_modified_at: 2021-04-04
redirect_from:
  - /docs/
---

PDFStitcher is written in Python and bundled into executables for Windows and Mac. It does not need to be installed; just download and run.

## Windows
[<i class='fas fa-download'></i> Download for Windows]({{ site.latest-windows }}){: .btn .btn--primary }

PDFStitcher should run on Windows 7 or newer. If your system blocks you from opening it, try [adding a security exclusion](https://support.microsoft.com/en-us/windows/add-an-exclusion-to-windows-security-811816c0-4dfd-af4a-47e4-c301afe13b26) or [following these instructions](https://www.windowscentral.com/how-fix-app-has-been-blocked-your-protection-windows-10).

After downloading pdfstitcher.exe, you can put it wherever you want - your desktop, your user folder, a cloud drive, etc. It is a self-contained executable so you just double click to run.

![windows desktop icon](/assets/images/windows-desktop.png)

## macOS
[<i class='fas fa-download'></i> Download for Mac (Intel)]({{ site.latest-mac-intel }}){: .btn .btn--primary }
[<i class='fas fa-download'></i> Download for Mac (M1/M2)]({{ site.latest-mac-apple-silicon }}){: .btn .btn--primary }

If you're using a Mac, PDFStitcher will only run on ~~OS X Catalina (10.15)~~ macOS 11 (Big Sur) or newer. The last release to support 10.15 was [v0.7.1](https://github.com/cfcurtis/pdfstitcher/releases/download/v0.7.1/PDFStitcher-Installer.dmg). 

You will likely get a warning that you are trying to open an app from an unidentified developer and you won't be able to run it right away. Please see [this article](https://support.apple.com/guide/mac-help/mh40616) for instructions on how to override this warning.

After downloading you can double click the .dmg and drag and drop pdfstitcher.app to your Applications folder (or again, it can really run from anywhere you want to put it). This is a new process as of v0.4 - older versions distribute the .app as a zip file.

![mac installer dmg](/assets/images/mac-install.png)

## Linux
PDFStitcher is available on Flathub. 

<a href='https://flathub.org/apps/details/com.github.cfcurtis.pdfstitcher'><img width='120' alt='Download on Flathub' src='https://flathub.org/assets/badges/flathub-badge-en.svg'/></a>

## Other
PDFStitcher can also be installed from [PyPi](https://pypi.org/project/pdfstitcher/) for Python 3.6-3.10 with the command:

```
pip install pdfstitcher
```

This will install pdfstitcher as a module and a script that can be launched with:

```
pdfstitcher
```

or 

```
python -m pdfstitcher
```

Note that this will not work with Python 3.11+ until wxPython is updated.

Finally, you can also download [previous releases](https://github.com/cfcurtis/pdfstitcher/releases) or the [source code](https://github.com/cfcurtis/pdfstitcher) from GitHub.
