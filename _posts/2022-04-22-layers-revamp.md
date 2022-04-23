---
title: "v0.6: Layers revamp"
last_modified_at: 2022-04-22
excerpt: "A quick overview of how layer processing works"
toc: true
release: 'v0.6.1'
---

The last few incremental releases have fixed some bugs while introducing others, and I realized it had come to that point in a programming project where I need to throw it all out and start over:

![XKCD flow chart showing a pretty standard and cheeky workflow](https://imgs.xkcd.com/comics/good_code.png)

Not quite, but the changes were pretty significant. In particular, layer processing has become a bit of a nightmare and it was high time I became more methodical about fixing it.

## How layer processing works
One of these days I'll write up some more detailed documentation, but here's the gist.

PDFs are pretty complicated. They can display text, images, interactive content, and (of particular interest for sewing patterns) vector graphics. The entire [specification](https://ghostscript.com/~robin/pdf_reference17.pdf) is currently over a thousand pages. To make things even trickier, every PDF is constructed a little bit differently, so PDFStitcher tries to check for the structures it knows about, but there are surely more.

Each page can be thought of as a list of commands to be read in order. PDFs are "stateful", which means that as you read through the commands, you need to maintain a running state representing how things are displayed. While a human might say "draw a black line", a PDF would say "henceforth, all lines shall be black", and then every line drawn after that command is black. To draw colours in multiple lines, styles, or thicknesses, a new state command needs to be issued.

### A simple example

Let's say a PDF looks like this:

![simple drawing of a two lines and a circle]({{'/assets/images/line-circle.svg' | relative_url}})

Ignoring layers for the moment, this might be constructed as follows:

- lines are black
- filled objects are red
- draw a line
- lines are green
- draw a circle and fill it
- draw a line

There could be variations on this order, so long as the line colour definition occurs before each line.

However, it's possible that one or more of the objects is actually in a separate object referenced from the page. This is common for repeating elements like logos that occur on multiple pages. In that case, you might have:

- lines are black
- filled objects are red
- draw a line
- insert a reference object

The definition of the line being green could be either in the set of page commands, *or* in the referenced object. This means that if you're trying to modify line properties, you need to remember what the state was when the object was inserted - and this might change if it's placed multiple times!

### Layers

Layers are the magic that allow us to have multiple sizes that can be switched on and off, but they do introduce more complication. When I started writing PDFStitcher, I thought I could just obliterate all the information in a layer that I didn't want, but as it turns out, the graphics state is still being updated when you're inside a layer (or "Optional Content Group", in PDF lingo). This means that layers are not necessarily independent! The workaround for this is to keep the commands related to graphics state but delete the ones that actually show things. As a result, deleting a layer might look something like this:

Original:

- lines are black
- filled objects are red
- enter the green line layer
  - lines are green
  - draw a line
- exit the green line layer

Deleted:

- lines are black
- filled objects are red
- enter the green line layer
  - lines are green
- exit the green line layer

Importantly, even after leaving the "green line layer", the graphics state still knows that all subsequent lines should be green. When it comes to modifying layers rather than just deleting them, I need to be extra careful. If, for example, PDFStitcher only changed `lines are green` to `lines are red`, then every line after that command will be drawn in red, not just the ones in that layer. The workaround here is to detect when we're exiting the green line layer and insert a new command to make the lines green again.

Of course, it would be too easy if this were the only way to do things. Remember those referenced objects I mentioned? Sometimes these have a label attached to them that says they're optional content, so instead of this:

- enter the green line layer
  - lines are green
  - draw a line
- exit the green line layer

you just have this:

- insert reference object with some obscure label

However, there is no indication in the command at this point that the object being inserted is actually an optional content object, you need to go and check the object itself (remembering exactly what the graphics state was at the time of insertion).

Oh, and each of these referenced objects can reference other objects recursively, just to make it interesting.

In short, this stuff is complicated. I just discovered that if an object is described as a transparency group, it will completely break the PDF if I try to change the fill colour, so for now I've just added a check to see if transparency is defined and disallow modifying the fill colour. Hopefully this will address some mysteriously broken patterns that have been reported!

## Download

If you've gotten this far (or just clicked the link), go ahead and give it a shot! Since it was quite a big change to the source code, I'm bumping the version number up a notch, but that doesn't mean there aren't more bugs to be squashed.

Edit: within hours, several people discovered that the macOS app wasn't behaving. Following the principles of [semantic versioning](https://semver.org/) as well as the rules of [PyPi](https://pypi.org/), v0.6 is quickly replaced by {{ page.release }}.

[<i class='fas fa-download'></i> Download for Windows](https://github.com/cfcurtis/pdfstitcher/releases/download/{{ page.release }}/pdfstitcher.exe){: .btn .btn--primary }

[<i class='fas fa-download'></i> Download for Mac](https://github.com/cfcurtis/pdfstitcher/releases/download/{{ page.release }}/PDFStitcher-Installer.dmg){: .btn .btn--primary }

You can report bugs through the [bug tracker](https://github.com/cfcurtis/pdfstitcher/issues), comment on the Facebook post in [Projectors for Sewing](https://www.facebook.com/groups/ProjectorsForSewing), leave a message on this post, or [email me](mailto:c.f.curtis@gmail.com) with feedback.


## Translations

As usual, translation files lag a bit behind the development. It will still work in your supported language, but the occasional message or label may show up in English as a result of changes. If you'd like to fix a translation, please see [this page](/docs/translate/).