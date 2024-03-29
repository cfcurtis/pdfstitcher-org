---
layout: splash
permalink: /
hidden: true
header:
  overlay_filter: linear-gradient(0deg, rgba(0,0,0,0.3),rgba(0,0,0,0.8) 50%)
  overlay_image: "assets/images/header.png"
  og_image: "assets/images/og_aspect_icon.png" 
  actions:
    - label: "<i class='fas fa-download'></i> Windows"
      url: "https://github.com/cfcurtis/pdfstitcher/releases/latest/download/pdfstitcher.exe"
    - label: "<i class='fas fa-download'></i> Mac (Intel)"
      url: "https://github.com/cfcurtis/pdfstitcher/releases/latest/download/PDFStitcher-InstallerX64.dmg"
    - label: "<i class='fas fa-download'></i> Mac (M1/M2)"
      url: "https://github.com/cfcurtis/pdfstitcher/releases/latest/download/PDFStitcher-InstallerARM64.dmg"
    - label: "<img width='120' alt='Download on Flathub' src='https://flathub.org/assets/badges/flathub-badge-en.svg'/>"
      url: "https://flathub.org/apps/details/com.github.cfcurtis.pdfstitcher"
excerpt: >
  The open source PDF stitching software for sewists, by sewists.<br />
  <small><a href="https://github.com/cfcurtis/pdfstitcher/releases/latest">Latest release: v0.9.2</a></small>
feature_row:
  - title: macOS issue (mostly) solved
    excerpt: "With the release of 0.9.2, the issue with encrypted PDFs and Intel macs has been patched. If you're curious, you can read more below."
    url: "/intel-mac-issue/"
    btn_class: "btn--primary"
    btn_label: "Learn more"
  - title: <a href="/docs/tutorials/"><img src="/assets/images/tutorial.png" alt="tutorials" /></a>
    excerpt: "Tutorials available in English, German and Czech!"
    btn_class: ""
    btn_label: ""
  - title: <a href="/contribute/"><i class="fas fa-hands-helping fa-5x"></i></a>
    excerpt: "Want to contribute to PDFStitcher?"
    url: "/docs/contribute/"
    btn_class: "btn--primary"
    btn_label: "Learn more"
---

{% include feature_row %}
