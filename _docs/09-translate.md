---
permalink: /docs/translate
title: "Translations"
last_modified_at: 2021-04-10
---

## Overview
PDFStitcher uses [GNU gettext](https://docs.python.org/3/library/gettext.html) for translation, but you don't need to be a programmer to contribute. The way translations work is:

1. The programmer uses a special function to write all the strings in their native language (in this case, English). Strings are text elements like labels and messages.
2. When the program is updated and ready for translation, a ".pot" file is created with a list of all the strings.
3. When a new language is added, a ".po" file is created with a list of each English string and a corresponding blank string ("") to fill in with the other language.
4. The translator fills in the blanks using a text editor or [Poedit](https://poedit.net).
5. The programmer takes the completed .po file and compiles it in to the program.

PDFStitcher will read your system language and display the correct translation accordingly, if it is supported. If not, consider [adding one](#adding-a-new-translation).

## Editing an existing translation file
There are two ways to edit .po files. The easiest way to edit them is [Poedit](https://poedit.net), but if you don't want to install new software you can also just edit the text file directly.

When you're done editing the .po file you can [email it to me](mailto:c.f.curtis@gmail.com), or if you're comfortable using git feel free to upload it directly to [github]({{ site.github.repository_url }}). Don't worry about making mistakes - the beauty of version control is we can always go back and fix things.

{% capture notice-text %}
**Important:** Some of the English messages have placeholders in them as "{}", which the code will fill in with the appropriate value. The translated version must have the same number of placeholders, otherwise the code will break.

Example: "Tiling with {} rows and {} columns"/"Carrelage avec {} lignes et {} colonnes". 
{% endcapture %}

<div class="notice--info">
  {{ notice-text | markdownify }}
</div>

### Poedit
![poedit screenshot](/assets/images/09-translate-img1.png)

Above is an example of what you might see if you open a partially completed translation file with Poedit. You can click on each row to edit the corresponding translation, and the entries can be sorted from the "View" menu to show suspected errors or missing values first.

### Text editor
You can edit the .po file directly in a text editor by right clicking the file, choosing "Open With", and selecting "Notepad":

![open in notepad](/assets/images/09-translate-img2.png)

On macOS the application is called "TextEdit". You can also open run the application first and then open the file with the File->Open menu.

Once the file is opened, you'll see something like the following:

![po file in notepad](/assets/images/09-translate-img3.png)

There is some header information that you can ignore followed by pairs of "msgid" (English string) and "msgstr" (translated). I've highlighted an empty msgstr - this is where you can fill in the translated version in your language.

There are also comments in this file like the one circled in red. Any line that begins with a \# is a comment and can be ignored, even if it says "msgid" or "msgstr".

## Adding a new translation
If you'd like to add a new language, thank you! Let me know by submitting an [issue]({{ site.github.issues_url }}) or sending me an [email](mailto:c.f.curtis@gmail.com) and I'll create a new .po file for your language.