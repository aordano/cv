# CV / Resumé

Hi! This is my resumé. It is written on and based off Xavier Danaux's [Modern CV Template](https://www.latextemplates.com/template/moderncv-cv-and-cover-letter).

The graphics are made in Adobe Illustrator and imported natively into the TeX file.

## Requirements

To build this file you need a LaTeX distribution on your PATH, and several packages. It is recommended to have a full install or enable on-the-fly installation of packages (for some reason this uses a ton of them).

You also need `xelatex` (and `xdvipdfmx` configured to render GhostScript in unsafe mode, plus `pdf2htmlex` if you want HTML output) in your PATH.

I provide some VSCode LaTeX Workshop recipes to ease the build.

Also you need `Helvetica Neue LT Std` and the `CMU` fonts installed on your system.

## Build

To build this, either use the provided recipes or:

### Only PDF

``` bash
$ xelatex -synctex=1 -interaction=nonstopmode -file-line-error -output-directory=build cv.tex
$ xelatex -synctex=1 -interaction=nonstopmode -file-line-error -output-directory=build cv.tex
```

### PDF and HTML

``` bash
$ xelatex -synctex=1 -interaction=nonstopmode -file-line-error -output-directory=build -no-pdf cv.tex
$ xelatex -synctex=1 -interaction=nonstopmode -file-line-error -output-directory=build -no-pdf cv.tex
$ xdvipdfmx -v -E -D "rungs -dEmbedAllFonts=true -dMaxSubsetPct=100 -dSubsetFonts=true -dInterpolateControl=-1 -dWRITESYSTEMDICT -dNOOUTERSAVE -dALLOWPSTRANSPARENCY -dSAFER --permit-file-all=/usr/share/texfm-dist/* -dNOPAUSE -dBATCH -dEPSCrop -sPAPERSIZE=a0 -sDEVICE=pdfwrite -dCompatibilityLevel=%v -dAutoFilterGrayImages=false -dGrayImageFilter=/FlateEncode -dAutoFilterColorImages=false -dColorImageFilter=/FlateEncode -dAutoRotatePages=/None -dDOPDFMARKS -sOutputFile='%o' '%i' -c quit"
$ pdf2htmlex cv.pdf --process-outline=0 --dest-dir=build
```

Yeah well sorry for the arcane incantations, you really should just use the recipes.