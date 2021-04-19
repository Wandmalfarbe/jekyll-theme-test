---
title: Basic Example
parent: Examples
...

# Basic Example

## Command

``` bash
# No lang option (-V lang=jp) here because Japanese unsupported in polyglossia.
pandoc "document.md" -o "document.pdf" --from markdown --template "../../eisvogel.tex" --listings --pdf-engine "xelatex" -V CJKmainfont="HiraginoSans-W4"
```

## Preview

[![](preview.png)](document.pdf)