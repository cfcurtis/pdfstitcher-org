---
permalink: /docs/layers
title: "Working with Layers"
last_modified_at: 2021-04-11
---

{% include figure image_path="/assets/images/06-layers-img1.png" alt="layers screenshot" caption="Sample pattern used by permission from Cathleen Hutch of [Sunny Mountain Patterns](https://www.etsy.com/shop/sunnymountainpattern)" %}

When a PDF with layers is loaded, this tab will list the layers detected in the document and present the option to apply line style modifications. The checkbox next to each layer name indicates whether it is to be included in the output.

## Checkboxes
**Include non-optional content**: Deselecting this layer will remove background information that is not in a layer.

**Deselect/select all**: By default all layers are selected. This box is provided for convenience as it can often be easier to deselect all and then select the ones you want.

## Line properties
Line colour, thickness, and style can be modified in many (but not all) PDFs. The checkbox next to each property indicates whether the modification will be applied - for example, you could increase the line thickness of all layers in the document without modifying colour or style by checking only the "Line Thickness" box.

The line properties can be applied to all checked layers by pressing "Apply to checked", while a single layer can be modified by clicking on the row and highlighting it. The "Apply" button will change to show the name of the selected row. After applying, the Line Properties column will fill in with the selected modifications.

## Example
In the example shown below, the Notes, 18M, and registration marks layers are selected for inclusion in the final PDF, while the 18M layer also has line property modifications.

![line properties example](/assets/images/06-layers-img2.png)