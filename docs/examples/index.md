---
title: Examples
nav_order: 4
has_toc: false
has_children: true
...

# Examples
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

## Numbered Sections

For PDFs with [numbered sections](http://pandoc.org/MANUAL.html#options-affecting-specific-writers) use the `--number-sections` or `-N` option.

``` bash
pandoc example.md -o example.pdf --template eisvogel --number-sections
```

## Syntax Highlighting with Listings

You can get syntax highlighting of delimited code blocks by using the LaTeX package listings with the option `--listings`. This example will produce the same syntax highlighting as in the example PDF.

``` bash
pandoc example.md -o example.pdf --template eisvogel --listings
```

## Syntax Highlighting Without Listings

The following examples show [syntax highlighting of delimited code blocks](http://pandoc.org/MANUAL.html#syntax-highlighting) without using listings. To see a list of all the supported highlight styles, type `pandoc --list-highlight-styles`.

``` bash
pandoc example.md -o example.pdf --template eisvogel --highlight-style pygments
```

``` bash
pandoc example.md -o example.pdf --template eisvogel --highlight-style kate
```

``` bash
pandoc example.md -o example.pdf --template eisvogel --highlight-style espresso
```

``` bash
pandoc example.md -o example.pdf --template eisvogel --highlight-style tango
```

## Standalone LaTeX Document

To produce a standalone LaTeX document for compiling with any LaTeX editor use `.tex` as an output file extension.

``` bash
pandoc example.md -o example.tex --template eisvogel
```

## Changing the Document Language

The default language of this template is American English. The `lang` variable identifies the main language of the document, using a code according to [BCP 47](https://tools.ietf.org/html/bcp47) (e.g. `en` or `en-GB`). For an incomplete list of the supported language codes see [the documentation for the hyph-utf8 package (Section 2)](http://mirrors.ctan.org/language/hyph-utf8/doc/generic/hyph-utf8/hyph-utf8.pdf). The following example changes the language to British English:

``` bash
pandoc example.md -o example.pdf --template eisvogel -V lang=en-GB
```

The following example changes the language to German:

``` bash
pandoc example.md -o example.pdf --template eisvogel -V lang=de
```

## Typesetting a Book

To typeset a book supply the template variable `-V book` from the command line or via `book: true` in the metadata.

To get the correct chapter headings you need to tell pandoc that it should convert first level headings (indicated by one `#` in markdown) to chapters with the command line option `--top-level-division=chapter`. Chapter numbers start at 1. If you need to change that, specify `first-chapter` in the template variables.

There will be one blank page before each chapter because the template is two-sided per default. So if you plan to publish your book as a PDF and don’t need a blank page you should add the class option `onesided` which can be done by supplying a template variable `-V classoption=oneside`.

## Example Images

| A green title page | A background image on the title page |
| :----------------: | :----------------: |
| [![A green title page](../examples/green-titlepage/green-titlepage.png)](../examples/green-titlepage/green-titlepage.pdf) | [![A background image on the title page](../examples/titlepage-background/titlepage-background.png)](../examples/titlepage-background/titlepage-background.pdf) |

| images and tables | Code blocks styled without listings |
| :---------------: | :---------------: |
| [![images and tables](../examples/images-and-tables/images-and-tables.png)](../examples/images-and-tables/images-and-tables.pdf) | [![Code blocks styled without listings](../examples/without-listings/without-listings.png)](../examples/without-listings/without-listings.pdf) |

| A book | Code blocks styled with listings |
| :----: | :----: |
| [![A book](../examples/book/book.png)](../examples/book/book.pdf) | [![Code blocks styled with listings](../examples/listings/listings.png)](../examples/listings/listings.pdf) |

| A background images on all pages | CJK Support (when using XeLaTeX) |
| :----: | :----: |
| [![A background images on all pages](../examples/page-background/page-background.png)](../examples/page-background/page-background.pdf) | [![CJK Support (when using XeLaTeX)](../examples/japanese/japanese.png)](../examples/japanese/japanese.pdf) |