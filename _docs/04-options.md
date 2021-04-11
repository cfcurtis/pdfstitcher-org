---
permalink: /docs/options
title: "Global Options"
last_modified_at: 2021-04-10
---

{% include figure image_path="/assets/images/04-options-img1.png" alt="options screenshot" caption="Sample pattern used by permission from Cathleen Hutch of [Sunny Mountain Patterns](https://www.etsy.com/shop/sunnymountainpattern)" %}

## Select input/output
To load a PDF, click "Select Input PDF" and browse to your pattern file. Similarly, clicking "Save output as" will open a file browser that lets you select a new file to save. Unlike most programs, you only define the output path once and it is re-written every time you click "Generate PDF". This allows you to quickly test out different parameters without prompting for the file name each time, as this can take some trial and error.

Note that PDFStitcher does not allow you to overwrite the original file, so the output file name must be different from the input.

**Tip:** you can also select an input PDF and output filename by using the File menu or keyboard shortcuts Ctrl/&#8984;+O and Ctrl/&#8984;+S. This works from any tab. 
{: .notice--info}

## Page range
After loading a file page range box is automatically populated with the entire range of the document (in this case, pages 1-25). Often, pattern pages are at the end of instructions, so you can define the pages of interest here. This field supports a combination of comma-separated lists and hyphenated ranges, e.g. 1-5, 8, 10-12. You can also define the pages out of order, repeat pages, or add blank pages by adding a zero to the list. More details on why you might want to do this can be found in the [page tiling](/docs/tiling) documentation.

## Checkboxes
Depending on what you want to do with PDFStitcher you can select "Tile Pages", "Process Layers", both, or neither:

### Process layers
Checking this applies the options selected in the Layers tab, outputting only the desired layers and/or applying line property modifications.

### Tile pages
Checking this applies all the options selected in the tile pages tab, assembling your pages to create a single large page. If you're processing a projector file that is already one page but you want to add margins, check this box.

### Unchecking both
If you run PDFStitcher without selecting either checkbox, the program will simply save a new file with your selected page range. This can be helpful to separate pattern pages from instructions, or to "unlock" a PDF to allow annotations.

**Note:** Unlocking a PDF can be useful to take your own notes. However, please respect the intellectual property of the pattern designer; PDFStitcher may not be used to modify and redistribute a pattern that has been purchased.
{: .notice--info}
