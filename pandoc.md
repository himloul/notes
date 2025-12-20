## Pandoc

*Commands cheat sheet*

Convert DOCX to Markdown using Github Flavored styling:

```sh
pandoc input.docx -f docx -t gfm --wrap=none -o output.md
```

Convert Markdown to HTML using Github Flavored Markdown styling:

```sh
pandoc -f gfm -t html5 -s --katex input.md -o output.html
```

Convert Markdown to docx and using a Company template:

```sh 
pandoc doc.md -o output.docx --reference-doc=company-template.docx --toc --number-sections
```

Convert Markdown to PDF using the sfdefault font, and add spacing to table:

```sh 
pandoc doc.md -o output.pdf --pdf-engine=xelatex -V header-includes="\renewcommand{\familydefault}{\sfdefault}" -V header-includes="\renewcommand{\arraystretch}{2.0}"
```
