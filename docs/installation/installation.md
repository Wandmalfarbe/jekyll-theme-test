---
title: Installation
nav_order: 1
has_children: true
has_toc: false
...

## Installation

1.  Install pandoc from <http://pandoc.org/>. You also need to install [LaTeX](https://en.wikibooks.org/wiki/LaTeX/Installation#Distributions).
2.  Download the latest version of the Eisvogel template from [the release page](https://github.com/Wandmalfarbe/pandoc-latex-template/releases/latest).
3.  Extract the downloaded ZIP archive and open the folder.
4.  Move the template `eisvogel.tex` to your pandoc templates folder and rename the file to `eisvogel.latex`. The location of the templates folder depends on your operating system:
      - Unix, Linux, macOS: `/Users/USERNAME/.local/share/pandoc/templates/` or `/Users/USERNAME/.pandoc/templates/`
      - Windows Vista or later: `C:\Users\USERNAME\AppData\Roaming\pandoc\templates\`

    If there are no folders called `templates` or `pandoc` you need to create them and put the template `eisvogel.latex` inside. You can find the default user data directory on your system by looking at the output of `pandoc --version`.