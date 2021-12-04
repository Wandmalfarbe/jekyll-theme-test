---
title: Book
parent: Examples
...

# Book

To typeset a book supply the template variable `-V book` from the command line or via `book: true` in the metadata.

To get the correct chapter headings you need to tell pandoc that it should convert first level headings (indicated by one `#` in markdown) to chapters with the command line option `--top-level-division=chapter`. Chapter numbers start at 1. If you need to change that, specify `first-chapter` in the template variables.

There will be one blank page before each chapter because the template is two-sided per default. So if you plan to publish your book as a PDF and don’t need a blank page you should add the class option `onesided` which can be done by supplying a template variable `-V classoption=oneside`.

{% include example-footer.md %}
