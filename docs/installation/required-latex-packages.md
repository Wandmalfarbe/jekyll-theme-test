---
title: Required LaTeX Packages
parent: Installation
...

# Required LaTeX Packages

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

## Texlive

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

## MiKTeX

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