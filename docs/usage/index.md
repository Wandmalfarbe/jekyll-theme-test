---
title: Usage
nav_order: 3
has_children: false
has_toc: false
...

# Usage
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

---

## Getting Started

1.  Open the terminal and navigate to the folder where your markdown file is located.

2.  Execute the following command

    ``` bash
    pandoc example.md -o example.pdf --from markdown --template eisvogel --listings
    ```

    where `example.md` is the markdown file you want to convert to PDF.

In order to have nice headers and footers you need to supply metadata to your document. You can do that with a [YAML metadata block](http://pandoc.org/MANUAL.html#extension-yaml_metadata_block) at the top of your markdown document (see the [example markdown file](../examples/basic-example/basic-example.md)). Your markdown document may look like the following:

``` markdown
---
title: "The Document Title"
author: [Example Author, Another Author]
date: "2017-02-20"
keywords: [Markdown, Example]
...

Here is the actual document text...
```

## Custom Template Variables

This template defines some new variables to control the appearance of the resulting PDF document. The existing template variables from pandoc are all supported and their documentation can be found in [the pandoc manual](https://pandoc.org/MANUAL.html#variables-for-latex).

  - `titlepage` (defaults to `false`)

    turns on the title page when `true`

  - `titlepage-color`

    the background color of the title page. The color value must be given as an HTML hex color like `D8DE2C` without the leading number sign (`#`). When specifying the color in YAML, it is advisable to enclose it in quotes like so `titlepage-color: "D8DE2C"` to avoid the truncation of the color (e.g. `000000` becoming `0`).

  - `titlepage-text-color` (defaults to `5F5F5F`)

    the text color of the title page

  - `titlepage-rule-color` (defaults to `435488`)

    the color of the rule on the top of the title page

  - `titlepage-rule-height` (defaults to `4`)

    the height of the rule on the top of the title page (in points)

  - `titlepage-background`

    the path to a background image for the title page. The background image is scaled to cover the entire page. In the examples folder under `titlepage-background` are a few example background images.

  - `page-background`

    the path to a background image for any page. The background image is scaled to cover the entire page. In the examples folder under `page-background` are a few example background images.

  - `page-background-opacity` (defaults to `0.2`)

    the background image opacity

  - `caption-justification` (defaults to `raggedright`)

    justification setting for captions (uses the `justification` parameter of the [caption](https://ctan.org/pkg/caption?lang=en) package)

  - `toc-own-page` (defaults to `false`)

    begin new page after table of contents, when `true`

  - `listings-disable-line-numbers` (defaults to `false`)

    disables line numbers for all listings

  - `listings-no-page-break` (defaults to `false`)

    avoid page break inside listings

  - `disable-header-and-footer` (default to `false`)

    disables the header and footer completely on all pages

  - `header-left` (defaults to the title)

    the text on the left side of the header

  - `header-center`

    the text in the center of the header

  - `header-right` (defaults to the date)

    the text on the right side of the header

  - `footer-left` (defaults to the author)

    the text on the left side of the footer

  - `footer-center`

    the text in the center of the footer

  - `footer-right` (defaults to the page number)

    the text on the right side of the footer

  - `footnotes-pretty` (defaults to `false`)

    prettifies formatting of footnotes (requires package `footmisc`)

  - `footnotes-disable-backlinks` (defaults to `false`)

    disables making the reference from the footnote at the bottom of the page into a link back to the occurence of the footnote in the main text (enabling requires package `footnotebackref`).

  - `book` (defaults to `false`)

    typeset as book

  - `logo`

    path to an image that will be displayed on the title page. The path is always relative to where pandoc is executed. The option `--resource-path` has no effect.

  - `logo-width` (defaults to `100`)

    the width of the logo (in points)

  - `first-chapter` (defaults to `1`)

    if typesetting a book with chapter numbers, specifies the number that will be assigned to the first chapter

  - `float-placement-figure` (defaults to `H`)

    Reset the default placement specifier for figure environments to the supplied value e.g. `htbp`. The available specifiers are listed below. The first four placement specifiers can be combined.

    1.  `h`: Place the float *here*, i.e., approximately at the same point it occurs in the source text.
    2.  `t`: Place the float at the *top* of the page.
    3.  `b`: Place the float at the *bottom* of the page.
    4.  `p`: Place the float on the next *page* that will contain only floats like figures and tables.
    5.  `H`: Place the float *HERE* (exactly where it occurs in the source text). The `H` specifier is provided by the [float package](https://ctan.org/pkg/float) and may not be used in conjunction with any other placement specifiers.

  - `table-use-row-colors` (defaults to `false`)

    enables row colors for tables. The default value is `false` because the coloring extends beyond the edge of the table and there is currently no way to change that.

  - `code-block-font-size` (defaults to `\small`)

    LaTeX command to change the font size for code blocks. The available values are `\tiny`, `\scriptsize`, `\footnotesize`, `\small`, `\normalsize`, `\large`, `\Large`, `\LARGE`, `\huge` and `\Huge`. This option will change the font size for default code blocks using the verbatim environment and for code blocks generated with listings.

## Common Errors

The following section lists common errors and their solutions when using the
Eisvogel template.

### LaTeX Errors `Missing endcsname inserted` or `File x not found` when using `titlepage-background` or `logo`

``` latex
Error producing PDF.
! Missing endcsname inserted.
<to be read again>
                   protect
```

``` latex
Error producing PDF.
! Package pdftex.def Error: File `logo\T1\textunderscoreimage.pdf' not fou
nd: using draft setting.

See the pdftex.def package documentation for explanation.
Type  H <return>  for immediate help.
```

These errors occur when one includes a background image on the title page or a
logo that has an underscore (`_`) in the filename.

A quick fix would be to replace all underscores in the filename of the image
with a hyphen (`-`). If the background image is specified in your YAML front
matter like so,

``` yaml
titlepage-background: "background_image.pdf"
```

you can advise pandoc to interpret this as LaTeX and include it in the document
without parsing.

``` yaml
titlepage-background: "`background_image.pdf`{=latex}"
```

The same fix can be used for the logo image as well:

``` yaml
logo: "`logo_image.pdf`{=latex}"
```

Corresponding issues:

- [Wandmalfarbe/pandoc-latex-template#100](https://github.com/Wandmalfarbe/pandoc-latex-template/issues/100)
- [Wandmalfarbe/pandoc-latex-template#166](https://github.com/Wandmalfarbe/pandoc-latex-template/issues/166)

### LaTeX Error `Missing \begin{document}`

```
! LaTeX Error: Missing \begin{document}.

See the LaTeX manual or LaTeX Companion for explanation.
Type  H <return>  for immediate help.
 ...

l.7 <
     !DOCTYPE html>
!  ==> Fatal error occurred, no output PDF file produced!
```

This error indicates that you try to use some text file for conversion that is
not the Eisvogel template. Please download the [latest Eisvogel template](https://github.com/Wandmalfarbe/pandoc-latex-template/releases/latest) from the releases page and start the conversion again.

### LaTeX Error `auto expansion is only possible with scalable fonts`

``` latex
Error producing PDF.
! pdfTeX error (font expansion): auto expansion is only possible with scalable
fonts.
\AtBegShi@Output ...ipout \box \AtBeginShipoutBox
                                                  \fi \fi
l.643 \begin{lstlisting}
```

This error likely occurs on Windows with MiKTeX installed. StackOverflow user
[Krebto provided the following fix](https://tex.stackexchange.com/a/392467):

> To solve the problem navigate to `C:\Program Files\MiKTeX 2.9\miktex\bin\x64` and run `updmap.exe`. The program may seem as it hangs for a while, but its probably because it tries to update the whole font tree. This solved the problem for me. After re-compiling everything should work fine.

Corresponding issue:

- [Wandmalfarbe/pandoc-latex-template#133](https://github.com/Wandmalfarbe/pandoc-latex-template/issues/133)

### LaTeX Error `cannot find image file`

``` latex
Error producing PDF.
! error:  (file "/tmp/tex2pdf.-be734e802ef6d0c3/""fdcfc29edcf252186f1b0a52f18f50
43abaeb2d0".png) (pdf backend): cannot find image file '"/tmp/tex2pdf.-be734e802
ef6d0c3/""fdcfc29edcf252186f1b0a52f18f5043abaeb2d0".png'
!  ==> Fatal error occurred, no output PDF file produced!
```

In general this error means that LaTeX is unable to find the included image
file. Please check all image references and file names for correctness.

This error also occurs if you use an old version of Eisvogel with the package
`grffile` and have an old LaTeX distribution installed. Please update Eisvogel
and your LaTeX distribution.

Corresponding issues:

- [jgm/pandoc#5848](https://github.com/jgm/pandoc/issues/5848)
- [Wandmalfarbe/pandoc-latex-template#149](https://github.com/Wandmalfarbe/pandoc-latex-template/issues/149)