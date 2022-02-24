---
permalink: /docs/translate
title: "Translations"
last_modified_at: 2021-10-04
---

## Weblate
PDFStitcher is now translated using [Weblate](https://hosted.weblate.org/engage/pdfstitcher/)! You can create an account and edit translations directly on the website, no need to download text files or additional software. Select "User Interface" to see the status of the existing languages, make edits, or add new languages.

<a href="https://hosted.weblate.org/engage/pdfstitcher/">
<img src="https://hosted.weblate.org/widgets/pdfstitcher/-/open-graph.png" alt="Translation status" />
</a>

{% capture notice-text %}
**Important:** Some of the English messages have placeholders in them as "{}", which the code will fill in with the appropriate value. The translated version must have the same number of placeholders, otherwise the code will break.

Example: "Tiling with {} rows and {} columns"/"Carrelage avec {} lignes et {} colonnes". 
{% endcapture %}

<div class="notice--info">
  {{ notice-text | markdownify }}
</div>