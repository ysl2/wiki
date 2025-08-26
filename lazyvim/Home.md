# [lazyvim] Home

## firenvim

For firefox, `ctrl + shift + 6`:

<img src=".assets/Home/img/2025-07-13-16-45-58.png" alt="" width=100%>

<img src=".assets/Home/img/2025-07-13-16-46-39.png" alt="" width=100%>

## vimtex

### xelatex

The default latex compiler is latexmk, the default compile engine is pdflatex.

If you want to use `xelatex` (for Chinese support) as compile engine in specific project, you should add a `.latexmkrc` in your project root, then add this into this `.latexmkrc`:

```lua
$pdf_mode = 5;
```

This tells latexmk to use `xelatex` as this project's compile engine. the mode 5 represents xelatex. Check vimtex's help doc for more info.
