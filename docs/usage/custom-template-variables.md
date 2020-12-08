---
title: Custom Template Variables
parent: Usage
nav_order: 1
...

# Custom Template Variables

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
