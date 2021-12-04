---
title: Installation
nav_order: 2
has_children: false
has_toc: false
...

# Installation
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

1.  Install pandoc from <http://pandoc.org/>. You also need to install [LaTeX](https://en.wikibooks.org/wiki/LaTeX/Installation#Distributions).
2.  Download the latest version of the Eisvogel template from [the release page](https://github.com/Wandmalfarbe/pandoc-latex-template/releases/latest).
3.  Extract the downloaded ZIP archive and open the folder.
4.  Move the template `eisvogel.tex` to your pandoc templates folder and rename the file to `eisvogel.latex`. The location of the templates folder depends on your operating system:
      - Unix, Linux, macOS: `/Users/USERNAME/.local/share/pandoc/templates/` or `/Users/USERNAME/.pandoc/templates/`
      - Windows Vista or later: `C:\Users\USERNAME\AppData\Roaming\pandoc\templates\`

    If there are no folders called `templates` or `pandoc` you need to create them and put the template `eisvogel.latex` inside. You can find the default user data directory on your system by looking at the output of `pandoc --version`.
5. To use the template follow the steps in the [Getting Started]({{ site.baseurl }}{% link usage/index.md %}#getting-started) section.

## Required LaTeX Packages

LaTeX manages addons and additional functionality in so called packages. You
might get the following error when compiling a document with the Eisvogel
template:


``` sh
! LaTeX Error: File `footnotebackref.sty' not found.

Type X to quit or <RETURN> to proceed,
or enter new name. (Default extension: sty)

Enter file name:
! Emergency stop.
<read *>
```

LaTeX informs you that the additional package `footnotebackref` is required to
render the document.

### Texlive

Eisvogel requires a full texlive distribution that can be installed by running
`apt-get install texlive-full` in the terminal. Because `texlive-full` is very
large (about 5 Gigabytes) you can also install the smaller texlive bundles and
add any missing packages manually.

A smaller texlive bundle is `texlive-latex-extra`. With `texlive-latex-extra`
you also need to install these packages manually:

```
adjustbox babel-german background bidi collectbox csquotes everypage filehook
footmisc footnotebackref framed fvextra letltxmacro ly1 mdframed mweights
needspace pagecolor sourcecodepro sourcesanspro titling ucharcat ulem
unicode-math upquote xecjk xurl zref
```

Install them with the following command:

``` sh
tlmgr install adjustbox babel-german background bidi collectbox csquotes everypage filehook footmisc footnotebackref framed fvextra letltxmacro ly1 mdframed mweights needspace pagecolor sourcecodepro sourcesanspro titling ucharcat ulem unicode-math upquote xecjk xurl zref
```

Additional information about the different texlive packages can be found at
this TeX-StackExchange answer: <https://tex.stackexchange.com/a/504566>

### MiKTeX

If you don't want to install all missing packages manually, [MiKTeX might be
an alternative](https://miktex.org/howto/miktex-console).

> MiKTeX has the ability to automatically install missing packages.
> You can turn this feature on or off. And you can let MiKTeX ask you each time a package has to be installed:
>
> - Click `Settings` to navigate to the settings page.
> - Click the `General` tab.
> - Click one of the radio buttons:
>     - `Ask me`
>     - `Always install missing packages on-the-fly`
>     - `Never install missing packages on-the-fly`