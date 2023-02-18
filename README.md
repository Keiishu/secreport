# secreport - Reports for the Computer Security course of the University of Namur
`secreport` is a $\LaTeX$ class that facilitates the writing of reports for the practical classes of the Computer Security course of the [University of Namur](https://unamur.be).

## Installation
To use this class, you can either compile `secreport.ins` with your favourite $\LaTeX$ compiler, or download the latest release to get `secreport.cls`. Then, **download a copy of the University's logo** [here](https://pds.unamur.be/presse/logos/unamur.png).

Once you have them, place them both in the root folder of your project and import the class in your main `.tex` file as you would import a normal document class, with `\documentclass[<options>]{secreport}`.

Similarly, to get a copy of the documentation, you can either compile `secreport.dtx` or get it from the latest release.

## Usage
A blank project with a pre-made structure is available in the `examples` folder as well as on [Overleaf](https://www.overleaf.com/read/gnnvbfvnkchs), where you can duplicate it for your own use.

Check the documentation for examples and more detailed instructions.

### File Structure
Simply create a folder in which you'll put your challenges as separate `.tex` files.
You can name it whatever you want, just be sure to tell the class with `\challengespath{<folder name>}`.

As you would probably have done it anyway, you have to name your challenges with a prefix. Again, whatever you want, but you probably want something simple. Use `\challengesprefix{<prefix>}` to setup your chosen prefix.

Once this is all set, use `\includechallenges{<num>}` in your document environment to import your challenges within your main file, `<num>` being the number of challenges you want to import.

#### **Example**
```
.
├── Challenges
│   ├── C1.tex
│   ├── C2.tex
│   ├── C3.tex
│   └── C4.tex
├── main.tex
├── unamur.png
└── secreport.cls
```
<details>
<summary>LaTeX header code</summary>

```LaTeX
\documentclass[12pt,a4paper,french]{secreport}

\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}

\challengespath{Challenges}
\challengesprefix{C}

\begin{document}
\includechallenges{4}
\end{document}
```
</details>

### Title page
The title page is typeset automatically by the class. The only thing you have to change is your report/group number, with `\reportnum{<num>}` and `\groupnum{<num>}` respectively.

Once both are set, use `\maketitle` in your document environment, as per usual.

### Text formatting
To quickly typeset simple code-like text (e.g. a filename with extension), you can use `\code{<text>}`.

To typeset paragraphs without a space between them, and without having to play
with the ``\parskip`` length, use the ```noparskip``` environment.

#### Highlighting source code
To highlight source code, this class imports the [minted](https://ctan.org/pkg/minted) package. It is advised to read the [original documentation](http://mirrors.ctan.org/macros/latex/contrib/minted/minted.pdf) to master it properly, as it is way more extensive than what is described here.

Use the `minted` environment to highlight multiple lines.
```LaTeX
\begin{minted}{<language>}
<code>
\end{minted}
```

Use `\mintinline{<language>}{<code>}` to highlight a single line of code.
This box will not break, so be careful about overfull boxes.

To import a whole file, use ```\inputminted{<language>}{<filename>}```.

## License
This work may be distributed and/or modified under the conditions of the [LaTeX Project Public License (LPPL)](http://www.latex-project.org/lppl.txt), version 1.3c or later.
