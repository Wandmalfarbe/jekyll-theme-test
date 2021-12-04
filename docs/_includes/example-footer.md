## Command

``` bash
{% include_relative /build.sh %}
```

## Markdown Document

{% capture exampleMarkdown %}{% include_relative /document.md %}{% endcapture %}

```` markdown
{{ exampleMarkdown }}
````

## Preview

[![](preview.png)](document.pdf)