# output html
```sh
pandoc foo.md -o foo.html
```

# output pdf
```sh
pandoc foo.md -o foo.pdf --latex-engine=xelatex -V mainfont='STHeiti'
```

# default template
```sh
pandoc -D latex > template.tex
```

# fix Erroneous variable \c__fontspec_shape_n_n_tl used!
* use MiKTeX Package Manager (Admin) to uninstall fontspec and reinstall fontspec
