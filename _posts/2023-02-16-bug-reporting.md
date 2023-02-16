---
title: "v0.8 now available for beta testing"
last_modified_at: 2023-02-16
excerpt: "New features for bug reporting, plus some bug fixes (of course)"
toc: true
release: 'v0.8b1'
---

As usual, I haven't updated either PDFStitcher or this site in far too long. Time to change both! I've got a new version available for beta testing, and I hope to be able to make it the official latest version soon. So, what took so long?

## Try out the beta version!

[<i class='fas fa-download'></i> Download for Windows](https://github.com/cfcurtis/pdfstitcher/releases/download/{{ page.release }}/pdfstitcher.exe){: .btn .btn--primary }

[<i class='fas fa-download'></i> Download for Mac (Intel)](https://github.com/cfcurtis/pdfstitcher/releases/download/{{ page.release }}/PDFStitcher-InstallerX64.dmg){: .btn .btn--primary }

New in v0.8 beta: native support for Apple Silicon (M1/M2) processors!

[<i class='fas fa-download'></i> Download for Mac (M1/M2)](https://github.com/cfcurtis/pdfstitcher/releases/download/{{ page.release }}/PDFStitcher-InstallerARM64.dmg){: .btn .btn--primary }

## Bug Reporting
One of the big challenges of writing PDF processing software is the incredibly complicated and inconsistent nature of PDFs. Additionally, sewing patterns are proprietary documents, so I can't ask users to send me a file to test with. This means that it's often very challenging to replicate the bug.

To address this problem, I wrote a utility called "pdf-mangler" (and [presented it](https://dl.acm.org/doi/abs/10.1145/3558100.3563849) at last year's Document Engineering Symposium) that reads through a PDF and strips out any identifying information to anonymize it. Then, it randomly replaces text with gibberish, distorts vector graphics, and replaces images with highly blurred versions - basically, it renders the document useless, but retains the structure. I am hoping that this will allow me to reproduce bugs without violating copyright agreements.

To access the mangling utility, there's a new menu item called "Report a Bug" under the "Help" menu. Selecting this brings up a dialog box with a bunch of information about your system, PDFStitcher configuration options, and any program output produced so far. It also has a section for you to fill in describing how to reproduce the problem, with suggested steps. Below the big fillable text box, there's a button to create a mangled PDF, which by default is placed on your desktop.

![Bug Reporting Dialog](/assets/images/bug-reporter.png)

To actually report the bug, press the "Report Via GitHub" button to create a new issue through GitHub (preferred, but requires a preference), or "Email to ccurtis@mtroyal.ca" to email to me directly. Either way, you'll have to copy the text from the dialog box and paste it into the issue or email, then (optionally) attach the mangled PDF. It's not quite as slick as a fully automated "submit a bug report" button, but it's a start.

## PDF Compliance
One thing that I didn't really consider when I created PDFStitcher was the permissions. It's not that I was intentionally trying to bypass restrictions, I just didn't realize that obeying the permissions on a PDF is up to the software. I've had many discussions in recent weeks with pattern designers and open source software developers, and there's no real consensus. Some designers want the permissions to be obeyed (e.g. if it says pages can't be rearranged, then tiling shouldn't be allowed), but others would prefer their patterns be usable in any way possible.

The real kicker for me is that with open source software, even if I added a permissions check and said "sorry, you can't modify this PDF", it would be trivial for another developer to fork my project, remove that chunk of code, and make a new version of PDFStitcher that ignores permissions.

As a compromise, I've settled on reading the permissions and informing the user of the author's preferences. I've also included a message reminding the user that PDFStitcher should be used for personal use only.

## Complete change log
You can see everything that's been changed in the GitHub release [here](https://github.com/cfcurtis/pdfstitcher/releases/tag/v0.8b1).

## Translations
As usual, translation files lag a bit behind the development. It will still work in your supported language, but the occasional message or label may show up in English as a result of changes. If you'd like to fix a translation, please see [this page](/docs/translate/).