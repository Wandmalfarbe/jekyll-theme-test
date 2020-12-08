---
title: Common Errors
parent: Usage
nav_order: 2
...

# Common Errors

The following section lists common errors and their solutions when using the
Eisvogel template.

## LaTeX Errors `Missing endcsname inserted` or `File x not found` when using `titlepage-background` or `logo`

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

## LaTeX Error `Missing \begin{document}`

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

## LaTeX Error `auto expansion is only possible with scalable fonts`

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

## LaTeX Error `cannot find image file`

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