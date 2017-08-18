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
