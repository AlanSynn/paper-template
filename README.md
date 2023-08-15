# A Repository for Academic Publication Templates in LaTeX

Welcome to a repository that harbors a selection of LaTeX templates tailored specifically for academic conferences. Among the supported formats are esteemed names such as ACM, IEEE, and USENIX. We have diligently tested these templates across a spectrum of conferences:
- ACM: CCS, SOCC, SOSP
- Eurosys
- IEEE's S&P
- USENIX: ATC, NSDI, OSDI, Security

## Necessary Tools

The journey to crafting a publication commences with equipping your system with essential programs:
- `pdflatex` compiles LaTeX into the venerable PDF.
- `bibtex` builds your bibliography.
- `latexmk` serves for incremental LaTeX compilation.
- `htlatex` caters to LaTeX-to-HTML transformation.
- `chktex` vigilantly lints your .tex manuscripts.

An OS-specific meta-package likely has all these tools bundled together. Installation guides for Ubuntu and MacOS are provided below.

Ubuntu:
```bash
$ sudo apt-get install texlive-full
```

MacOS:
```bash
$ brew cask install mactex
```

## Structuring Your Work

### Files and Folders

- The `paper.tex` is the core document to be compiled.
- The `paper.bib` acts as the BibTeX master of all references.
- The `sections/` houses the textual components of your paper.
- The `style/` directory holds the styling macros.

### Working with the Template

#### Abstracting the System's Name

For the sake of simplicity, the variable `\systemname{}` replaces the hard-coded system name, enabling future alterations.

#### Macros

Common packages, macros, and commands must reside in `style/head-common.tex`.

#### Adapting to Conference Styles

Three alterations in `paper.tex` adapt the formatting for your specific conference:
1. Header file inclusion (e.g. `\input{style/head-usenix}`)
2. Author list inclusion (e.g. `\input{author-usenix}`)
3. Bibliography style unveiling

### Crafting Sections

The art of sectioning involves creating new files within `sections/` and positioning them aptly in `paper.tex`.
```latex
...
\input{sections/design}
\input{sections/implementation}
...
```

### Compilation Essentials

Use the incremental compiler with:
```bash
$ make all
```

Manual compilation is also an option:
```bash
$ make complete   # Run pdflatex, bibtex, then pdflatex again
$ make pdf        # Run pdflatex once
$ make bib        # Run bibtex once
```

### Pre-Submission Checks

#### chktex and aspell

Run `chktex` and `aspell` on every `.tex` file in `sections/`. Shorthands are available:
```bash
$ make lint
```
```bash
$ aspell -c <filename>
```

#### Microsoft Word's Spell Check

Though unexpected in a LaTeX guide, MS Word's spell check still reigns supreme. Compile to HTML and use Word's spell check. Manual translation of changes back into `.tex` files is required.

Viewing the HTML file in a browser is facilitated by:
```bash
$ make serve
```

### Cleanup

The commands below aid in cleaning various files:
```bash
$ make clean        # Removes all non-version controlled files
$ make latexclean   # Cleans intermediate LaTeX files
```

## Your Contribution

Your improvements and adaptations are welcome. If you find yourself enhancing these templates, please extend your contributions to [alan@alansynn.com](mailto:alan@alansynn.com). Thank you!