---
title: Usage
has_children: true
...

# Usage

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