# TeXworks

## Install TeXworks (Editor)
* https://github.com/TeXworks/texworks/releases
* TeXworks 0.6.10
* Download and run `TeXworks-win10-setup-0.6.10-202502131411-git_7380941.exe`

## Install MiKTeX (Compiler)
* https://miktex.org/download
* Download and run `basic-miktex-25.12-x64.exe`

## Render in TeXworks
1. Open `*.tex`
2. Run `pdfLaTeX`
3. Run `BibTex`
4. Run `pdfLaTeX` twice

## Save difference between two tex files as PDF
Try `latexdiff --version`. If `latexdiff` is not installed, install it.
* Strawberry Perl https://strawberryperl.com/. Download and run `5.42.0.1 MSI`
```shell
git show abc1234:old_name.tex > old.tex # From commit hash
latexdiff --graphics-markup=none old.tex new.tex > diff.tex
# Compilte diff.tex
```