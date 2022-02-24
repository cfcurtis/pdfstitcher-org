---
title: "New release, new workflow"
last_modified_at: 2022-02-24
excerpt: "New workflow means more frequent releases"
toc: true
---

It's reading week in Canada, which means I was able to dedicate some time to PDFStitcher. The main improvements are to the workflow, both for translation and building releases, so hopefully future improvments can be incorporated faster with less time spent swapping between computers and manually uploading executables. Translations are now done through [Weblate](https://hosted.weblate.org/engage/pdfstitcher/), which allows you to edit the translation files right in the browser, while the Windows exe and macOS dmg are now built in a GitHub action so I can create a new release much faster than before.

The downside of all this automation is I am no longer using my old 2009 MacBook to build the macOS version, and the mac version of PDFStitcher will not run on macOS older than 10.15 (Catalina). This has become more and more difficult to support as all the tools and dependencies have been dropping support for older OS versions, and I apologize for those of you who won't be able to use newer versions on your older macs.

For Linux users, you can now get PDFStitcher on [FlatHub](https://flathub.org/apps/details/com.github.cfcurtis.pdfstitcher) or install via PyPi with the command:

```python
pip3 install pdfstitcher
```

This will allow you to run pdfstitcher as a script or a Python module:

```console
$ pdfstitcher
$ python3 -m pdfstitcher
```

## Download
With all that workflow stuff, there aren't too many changes to PDFStitcher itself - some new translations, improvements to the UI on high resolution displays, and the ability to open password-protected PDFs.

Get the 0.5.2 release here:

[<i class='fas fa-download'></i> Download for Windows](https://github.com/cfcurtis/pdfstitcher/releases/download/v0.5/pdfstitcher.exe){: .btn .btn--primary }

[<i class='fas fa-download'></i> Download for Mac](https://github.com/cfcurtis/pdfstitcher/releases/download/v0.5/PDFStitcher-Installer.dmg){: .btn .btn--primary }

You can report bugs through the [bug tracker](https://github.com/cfcurtis/pdfstitcher/issues), comment on the Facebook post in [Projectors for Sewing](https://www.facebook.com/groups/ProjectorsForSewing), leave a message on this post, or [email me](mailto:c.f.curtis@gmail.com) with feedback.


## Translations

As usual, translation files lag a bit behind the development. It will still work in your supported language, but the occasional message or label may show up in English as a result of changes. If you'd like to fix a translation, please see [this page](/docs/translate/).