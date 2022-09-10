
```tex
\documentclass[a4paper]{article}
\usepackage[top=1.25in, bottom=1.25in, left=1in, right=3in]{geometry}

\title{Title}
\author{Author}
\date{Today}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\DeclareUnicodeCharacter{202F}{\,}
\usepackage[pipeTables=true]{markdown}

\begin{document}
\markdownInput{tableinput.md}
\end{document}
```

- tableinput.md


```markdown
## Some title

A few words before the table.

| Product                                   | Price   |
| :---------------------------------------- | :------ |
| Good                                      | 14 €/kg |
| Better                                    | 19 €/kg |
| Best                                      | 32 €/kg |

```

[出处](https://tex.stackexchange.com/questions/612198/render-markdown-tables-correctly)