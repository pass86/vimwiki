# Install MacTeX
```sh
brew cask install mactex
export PATH=$PATH:/usr/local/texlive/2019/bin/x86_64-darwin
```

# Output HTML
```sh
pandoc foo.md -o foo.html
```

# Output PDF
```sh
pandoc foo.md -o foo.pdf --pdf-engine=xelatex -V mainfont='Hack' -V CJKmainfont='Source Han Sans SC' -V papersize=A4 -V geometry:margin=1in colorlinks
```

# Default Template
```sh
pandoc -D latex > template.tex
```

# Fix Erroneous variable \c__fontspec_shape_n_n_tl used!
* Launch MiKTeX Package Manager (Admin) to uninstall fontspec and reinstall fontspec
