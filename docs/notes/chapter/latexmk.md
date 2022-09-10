### latexmk

-   [编译器配置](https://www.cxyzjd.com/article/bleedingfight/84946793#_3)

# 编译器配置

使用latexmk，可以实现LaTeX文档自动编译，指定输出目录等功能。 latexmk的参数可以在命令行指定，也可以在配置文件中指定。  
配置文件存放：

1.  系统目录，如 `/usr/local/lib/latexmk/LatexMk`，视系统设置而定。
2.  个人根目录， `$HOME/.latexmkrc`。
3.  当前LaTeX主文件所在目录，`.latexmkrc` 或 `latexmkrc` 均可。
4.  任何其他位置，执行 `latexmk` 时由 -r 参数指定。  
    配置环境变量(`latexmkrc`或者`.latexmkrc`)：

```bash
$pdf_mode = 1;
$pdflatex = "xelatex -file-line-error --shell-escape -src-specials -synctex=1 -interaction=nonstopmode %O %S;cp %D %R.pdf";
$recorder = 1;
#$pdf_previewer = "SumatraPDF -reuse-instance -inverse-search -a %O %S";
$pdf_previewer = "open -a %S";
#连续编译模式
$preview_continuous_mode = 1;
$pdf_update_method = 0;
$clean_ext = "synctex.gz acn acr alg aux bbl bcf blg brf fdb_latexmk glg glo gls idx ilg ind ist lof log lot out run.xml toc dvi";
$bibtex_use = 2;
$out_dir = "temp";
#指定生成PDF文件的文件名，可以与LaTeX主文件名不一致
#$jobname = "Book";
```

latexmk 会根据情况，自动执行多次编译。编译完成后不退出，处于等待状态，监视源文件。一旦有更新，会实时编译，并刷新PDF阅读器（要求阅读器支持，如evince支持）。编译生成的文件都会输出到`$out_dir`指定的目录。但是，将最终的PDF文件复制到当前目录（代码第2行最后的命令）。 使用

```bash
latexmk -c
```

可以清空临时文件。临时文件对应的扩展名由 $clean_ext 指定。
```bash
$latex = 'latex  %O  --shell-escape %S';
$pdflatex = 'pdflatex  %O  --shell-escape %S';
#或者
$set_tex_cmds( '--shell-escape %O %S' );
```
配置参考
[Latex 编译和编写方案配置 — latexmk + latexworkshop](https://blog.csdn.net/weixin_43852511/article/details/105007356)