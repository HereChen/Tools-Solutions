# 文档处理工具

## Pandoc

Pandoc 主页 <http://pandoc.org>. Pandoc 可以实现不同格式文档的相互转换, 支持的格式包括 markdown、HTML、LaTeX、docx、EPUB ODT等等.

### markdown 多个文档转换

```
pandoc src/markdown/*.md -o build/latex/content.tex
```

### markdown 转 LaTeX, 用 listings 包替换 verbatim

pandoc --listings src/markdown/*.md -o build/latex/content.tex

## LaTeX

### Windows 上编译缓慢, 经常卡在 eu1lmr.fd

删除 `texlive\2016\texmf-var\fonts\cache` 文件夹下字体缓存, 重新生成字体缓存, 执行 `texlive\2016\bin\win32\fc-cache.exe`[^latexCompileSlowly].

[^latexCompileSlowly]: [LaTeX编译卡顿怎么办？](https://www.zhihu.com/question/51999238/answer/135852542)

### listings 代码换行

添加 `breaklines=true` 后, 还是存在没有空格的 url 无法换行, 需设置 `breakatwhitespace=false`. 另外, 可以在代码换行的地方添加箭头标识换行[^pandocMarkdownToLatexCodeWrap].

```latex
\lstset{
    breaklines=true,
    % 箭头标识换行
    postbreak=\raisebox{0ex}[0ex][0ex]{\ensuremath{\color{red}\hookrightarrow\space}},
    breakatwhitespace=false
}
```

[^pandocMarkdownToLatexCodeWrap]: [Pandoc: Markdown to PDF, without cutting off code block lines that are too long](http://tex.stackexchange.com/questions/179926/pandoc-markdown-to-pdf-without-cutting-off-code-block-lines-that-are-too-long)
, [Code not wrapping in listings even though breaklines=true](http://tex.stackexchange.com/questions/174569/code-not-wrapping-in-listings-even-though-breaklines-true)
, [lstlisting line wrapping](http://tex.stackexchange.com/questions/116534/lstlisting-line-wrapping)


