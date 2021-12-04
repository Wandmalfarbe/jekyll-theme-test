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

## Standalone LaTeX Document

To produce a standalone LaTeX document for compiling with any LaTeX editor use `.tex` as an output file extension.

``` bash
pandoc example.md -o example.tex --template eisvogel
```

## Typesetting a Book

To typeset a book supply the template variable `-V book` from the command line or via `book: true` in the metadata.

To get the correct chapter headings you need to tell pandoc that it should convert first level headings (indicated by one `#` in markdown) to chapters with the command line option `--top-level-division=chapter`. Chapter numbers start at 1. If you need to change that, specify `first-chapter` in the template variables.

There will be one blank page before each chapter because the template is two-sided per default. So if you plan to publish your book as a PDF and don’t need a blank page you should add the class option `onesided` which can be done by supplying a template variable `-V classoption=oneside`.
