# Introduction to LaTeX

## What is LaTeX? Why should I use it? 

LaTeX is a type-setting system that is often used to write technical or scientific documents. LaTeX is able to nicely render complex mathematical formulas and other special symbols easily. Unlike other document creation software like Word, LaTeX handles the majority of the styling of the document automatically, so you can focus on your content and not have to worry about how it will look on the page.

If you have used document markup languages before, like HTML or Markdown, you may find that LaTeX works in a similar manner. 

# How to Use LaTeX
While you can install software to write and compile LaTeX locally on your machine, we will be using a free online tool called Overleaf to write our documents in this workshop. Overleaf has a number of benefits. Since it is cloud-based there is nothing to install and you can access your documents from anywhere. Additionally, Overleaf supports collaborating with others on your document (2 people can work on the same document for free) which is a great feature for pair-projects. 

## Creating your first LaTeX document in Overleaf

Sign into your Overleaf account (or sign up for one if you haven't already). Press the "New Project" button and click "Blank Project". You will be prompted to give your project a name, select a suitable name (ex. "First Project") and click "Create". 

When you create your project in Overleaf, the following code will be generated for you. 

```latex
\documentclass{article}
\usepackage[utf8]{inputenc}

\title{First Project}
\author{yourUsername} 
\date{October 2021}

\begin{document}

\maketitle

\section{Introduction}

\end{document}
```

This will create an 'article' style document, with a title the same as what you named your project, the author field will have your Overleaf username and the date will auto fill to the current month and year. You can change the displayed title, author name, or date by simply editing the text between the curly brackets for each command. To update the PDF preview, you'll need to recompile. To do this you can either press `Ctrl-S` or `Ctrl-Enter` on your keyboard, or press the green `Recompile` button at the top of the PDF preview window.  

Note: You can have LaTeX automatically date your work by using the `\today` command. Replace the text in `\date{}` with `\date{\today}`, this will automatically update the date to today's date at the time of compilation, UTC+0. 

You will notice that there is a heading on the page labelled "1 Introduction" this is generated because of the `\section{Introduction}` command. The title of the section is written in between the curly brackets at the end of the command. 

You can use `\sections{}` to organize your document. You can also create `\subsections{}` and `\subsubsections{}` to better organize your document if needed.

Let's try adding the following code to our document under the `\section{Introduction}` line to see what happens. 

```latex
\section{LaTeX basics}
\subsection{How to use sections, subsections}
\subsubsection{Creating a table of contents}
\subsection{Line breaks, page breaks}
```

We can see that we have some new sections added to our document, labelled with section numbering and different heading sizes that correspond to the document hierarchy. 

This neat structure allows us to easily add a table of contents to our document by adding a `\tableofcontents` command (add this in between the line with `\maketitle` and the first `\section{}` of your document).

```latex
% ... 
\begin{document}
\maketitle
\tableofcontents
\section{Introduction}
% ...
```

It doesn't make a lot of sense to have a document that only has headings and no content. We can add content to a section simply by writing underneath that section command, as we see below.

```latex
\section{Introduction}
This is a quick introduction to the LaTeX typesetting system. LaTeX is great for
 all kinds of writing, especially when you need to write out mathematical symbols
and equations. Another great thing about LaTeX is that it allows you to focus 
on the \textit{content} instead of the \textbf{styling}.

\section{LaTeX basics}
This is a section. Everything written below this command will be included in 
this section, until the next section command is found. 

\subsection{How to use sections, subsections}
This is a subsection within the LaTeX basics section. 
This subsection also has its own sub-subsection. 

\subsubsection{Creating a table of contents}
Using this document structure, LaTeX can automatically make a table of contents 
for us, that displays the headings and subheadings of our document. 

\subsection{Line breaks, page breaks}
In most text editors, you can signal a line break in your text by simply 
pressing enter. In LaTeX a line break won't be rendered unless you press 
enter twice or use the "newline" command. If you want to force a page 
break in your document, you need to use the "newpage" command.
```

You may notice in the code above that the text includes line breaks which aren't rendered to the final document. In LaTeX, to add a line break you'll need to either press enter twice (adding two line breaks in your code) or use the `\newline` command to insert a line break. 

You can also manually force the start of a new page using the `\newpage` command. For example, if we want our title and our table of contents to be on a different page than our content, we can add a `\newpage` command underneath the `\tableofcontents` command. 

### Text Styling in LaTeX

To do things like write *italicized text*, **bold text**, or underlined text in LaTeX, you can use the commands `\textit{}`, `\textbf{}` and `\underline{}`, respectively. 

The command `\emph{}` is also available. This is used to *emphasize* text. When used in regular text, this means italics;when used within italicized text this will mean regular text. The `\emph{}` command may also act a little differently in different LaTeX environments (for example, when making slides). 

## Lists
There are two major types of lists in LaTeX, ordered (or numbered) lists and unordered lists (bullet points). 

Ordered (numbered) lists are created using `enumerate` as follows

```latex
\begin{enumerate}
  \item The first item
  \item The second item
\end{enumerate}
```

Unordered lists, or lists of bullet points can be created using `itemize` as follows

```latex
\begin{itemize}
  \item an item
  \item another item
\end{itemize}
```

Lists can also be nested within one another to create sublists. These can be ordered or unordered.
To create a list like this in LaTeX
1. top-level item 1 
  - sub item
  - another sub item
2. top-level item 2
3. top-level item 3

We would use the following code

```latex
\begin{enumerate}
  \item top-level item 1
    \begin{itemize}
      \item sub item
      \item another sub item
    \end{itemize}
  \item top-level item 2
  \item top-level item 3
\end{enumerate}
```

## Comments in LaTeX
To write comments in your LaTeX document, use the `%` symbol. Anything written on the line after the `%` symbol will be ignored by the LaTeX compiler.  

```latex
% an example of a LaTeX comment
% comments can be helpful to make notes on things within your document
% without having them actually appear on the page
```

## Writing equations
There are a handful of ways to write equations and other mathematical symbols in LaTeX. All mathematical symbols and equations are written inside "mathmode". 

### Writing in-line equations

In-line equations are useful for equations or symbols that you want to display in-line with your text. For example, if you were explaining what a certain symbol in your equation means you would probably want to include that symbol in your text. 

You can use mathmode inline by surrounding your mathmode text with `\(\)` or `$$`. Note that these two options are completely equivalent.  

**Examples**

$x^2$  would be written `\(x^2\)` or `$x^2$`

$\pi$ would be written as `\(\pi\)` or `$\pi$`  

### Writing block equations

Block equations will show up centered, on a new line. Block equations are created by surrounding the equation with `\[\]` as in the examples below. 

```latex
% circumference of a circle, note that a space is needed after the \pi command
\[C = 2\pi r \]
```

The output of the above example should look similar to: 

$ C = 2\pi r $

```latex
% displays the quadratic formula
\[x = \frac{-b \pm \sqrt{b^2 - 4ac} }{2a}\]
```

$x = \frac{-b \pm \sqrt{b^2 - 4ac} }{2a}$

### Some useful mathematical notation
#### Fractions
To write fractions in LaTeX, you use the command `\frac{}{}` where the numerator is in the first set of curly brackets and the denominator is in the second. For example, 3/4 would be written as `\frac{3}{4}`

####Exponents
To write exponents in LaTeX, use the `^` symbol.  For example, a<sup>b</sup> would be written `a^b`

If the exponent is more than 1 character, you will need to surround it by curly brackets. a<sup>123</sup> would be `a^{123}`

#### Additional resources

[More details on mathmode](https://www.overleaf.com/learn/latex/Mathematical_expressions) and a [list of symbols you may need to use](https://www.overleaf.com/learn/latex/List_of_Greek_letters_and_math_symbols).

#### Tip! 
If you don't know what LaTeX command to use to write a given symbol you can use [Detexify](https://detexify.kirelabs.org/classify.html) to find out! 

For example: 

![Detexify Example](https://github.com/BrockDSL/Intro_to_LaTeX/blob/b034e25b8e2e25ce445df209fe737a71c9d1ec5c/resources/DetexifyExample.png?raw=true)


### Exercises/Try It Yourself Examples
Try writing the following equations in LaTeX!

\begin{equation}
    y = x_0 + \frac{1}{2} x_1 + 4x_2 + 5
\end{equation}

\begin{equation}
    y = \frac{1}{\sqrt{x - 2}}
\end{equation}

## Adding figures
You may wish to add images to your document, in order to do this you'll need to use the `graphicx` package. To add this to your document, add the line `\usepackage{graphicx}` under the `\documentclass{}` command at the top of your document.

To add an image to your document, you'll first need to upload it to Overleaf. Press the "upload" button on the left-side of the screen under "Menu" to upload your images. 

In most cases, you'll want to be able to write a caption for your image, as well as be able to reference your image in the text. To do this, we'll use the `figure` environment. In Overleaf, if you begin writing `\figure` a suggestion for "\begin{figure}` will show up, by pressing tab Overleaf will automatically insert the following template code for you.

```latex
\begin{figure}
    \centering
    \includegraphics{}
    \caption{Caption}
    \label{fig:my_label}
\end{figure}
```

To add your image, you'll need to specify the filename (or filepath) for the image within the `\includegraphics{}` command. 

You can also give it a caption by replacing the text in the `\caption{}` command. You'll want to give it a meaningful `\label{}` as well so it's easy to reference the figure later. 

```latex
\begin{figure}
    \centering
    \includegraphics{array.png}
    \caption{A zero-indexed array containing the characters of the word "hello"}
    \label{fig:hello-array}
\end{figure}
```

The `\label{}` we have given the figure will allow us to easily reference the image in our text. If we wanted to point out this diagram in our text we would use the `\ref{}` command. This command will automatically add the correct figure number to your text so the reader knows what figure to refer to. 

```latex
Figure \ref{fig:hello-array} depicts a character array containing the letters of the word "hello".
```

More information on adding images to your LaTeX documents can be found in the Overleaf Help Documents [here](https://www.overleaf.com/learn/latex/Inserting_Images).

## Tables

To create tables in LaTeX, it is easiest to use a table generator. These allow you to enter data in your tables and format them in an environment similar to a spreadsheet. You can then copy and paste the generated LaTeX code into your document. 

https://www.tablesgenerator.com/ is an easy to use LaTeX table generator. 


The toolbar in the Table Generator allows you to select the alignment of content within your table cells; bold, italicize, or underline content in cells; add or remove cell borders; merge cells together or split merged cells; and change the text or background colour of cells. 

![tables generator toolbar](https://github.com/BrockDSL/Intro_to_LaTeX/blob/b034e25b8e2e25ce445df209fe737a71c9d1ec5c/resources/tables-gen-toolbar.png?raw=true)

Let's say we want to make a small 2 column table showing corresponding X and Y values. 

You'll likely need to remove empty columns from your table, you can do that by right clicking the column you wish to delete and selecting Column > Remove Column(s). 

![Removing a column](https://github.com/BrockDSL/Intro_to_LaTeX/blob/b034e25b8e2e25ce445df209fe737a71c9d1ec5c/resources/remove-column.png?raw=true)

We can now fill in our data in the X and Y columns of our table. 

By default your table won't have any borders, so it will just appear as two columns of data. To add borders you can use the border tools in the toolbar at the top of the page. For this example we'll add all borders. 

![ctrl-click to add all borders to all cells](https://github.com/BrockDSL/Intro_to_LaTeX/blob/b034e25b8e2e25ce445df209fe737a71c9d1ec5c/resources/ctrl-click-for-borders.png?raw=true)

The resulting LaTeX code you'll copy into your document should look something like this. 

```latex
\begin{table}[]
\begin{tabular}{|l|l|}
\hline
X & Y \\ \hline
1 & 1 \\ \hline
2 & 4 \\ \hline
3 & 9 \\ \hline
\end{tabular}
\end{table}
```

We can copy this code into our LaTeX document by pressing the "Copy to Clipboard" button and then pasting it into our document. 

You may want to add a caption to your table, and you'll likely want to be able to reference the table in your text, as you can with figures. To do this, we'll need to add the `\caption{}` and `\label{}` commands to our `table` environment.  

Adding the `\caption{}` command above the `tabular` block will place the number and caption for the table _above_ the table. Adding the `\caption{}` below the `tabular` block will place it _below_ the table. 

LaTeX will automatically place the table where it thinks is best. You can change the way that LaTeX places the table by adding indicators in the square brackets next to `\begin{table}`. For now we'll add `\begin{table}[htbp]`. For more information on these commands, see [this webpage](https://www.overleaf.com/learn/latex/Positioning_of_Figures). This also applies to figures and algorithms. 

## Algorithms

LaTeX has dedicated tools for displaying algorithms through pseudocode. There are a number of LaTeX packages which do this, and they all work a little differently. For this workshop we will be looking at the `algorithm` and  `algorithmic` packages. For more information about the other algorithm packages available see [this page](https://www.overleaf.com/learn/latex/Algorithms). 

In order to use the `algorithm` and `algorithmic` packages, we'll have to include them at the top of our document. Between the  `\documentclass{article}` command and the `\title{}` command, add the lines `\usepackage{algorithmic}` and `\usepackage{algorithm}`.

We'll now practice writing out some simple pseudocode. 

```latex
%  an if -else statement 
\begin{algorithm}
    \caption{An if-else statement}
    \begin{algorithmic}
    \STATE $i \gets 10$
        \IF {$i < 5$}
          \STATE $i \gets i*2$
        \ELSE 
          \STATE $i \gets i-1$
        \ENDIF
    \end{algorithmic}
\end{algorithm}
```

Notice that all the commands (`\STATE`, `\IF{}`, `\ENDIF`, etc) are written in uppercase. 

`\gets` adds a left arrow ($\gets$) to indicate that we are storing a value. 

The `\STATE` command will display whatever is written beside it as written. In the above example, `$$` is used to enter mathmode allowing us to display the `\gets` arrow, and also displaying the variable i as $i$.   

The `\IF{}` command requires that the condition be placed within curly brackets. The if block is closed using the `\ENDIF` command.

```latex
\begin{algorithm}
    \caption{A while loop}
    \begin{algorithmic}
        \STATE $i \gets 10$
        \WHILE {$i > 0$}
            \STATE print $i$
            \STATE $i \gets i-1$
        \ENDWHILE
    \end{algorithmic}
\end{algorithm}
```

Similar to the `\IF{}` command, the `WHILE{}` command also requires that the condition be placed within curly brackets and the block is ended with `\ENDWHILE`. 

## Citations, Bibliographies, Citation Managers and BibTeX

When writing academic papers it is crucial that you always cite your sources. Using LaTeX makes the process of citing appropriately very easy. 

Let's start by discussing the bibliography, or the list of all your sources, which comes at the end of your paper. There are a couple of ways you can create this in LaTeX, either by hand or by using a citation management software. 

We can see an example of a handwritten bibliogrpahy in the IEEE Conference Paper Template. The bibliography is contained within the `bibliography` block. Each item in the bibliography is a `\bibitem{}` with a label inside the {} which can be used to cite that source in your writing. To cite a source in your writing, use the `\cite{}` command, and add the label from the `\bibitem{}` inside the curly braces. 

```latex
\usepackage{cite} %needed to use the \cite{} command

% an example of a line where you may wish to cite something in your bibliography
A good reference for technical writing is \cite{tech-writing}.  

% modified from the bibliography of the IEEE conference paper template
\begin{thebibliography}
    \bibitem{tech-writing} M. Young, The Technical Writer's Handbook. Mill Valley, CA: University Science, 1989.
\end{thebibliography}
```

If your bibliography is quite small, writing out the whole thing by hand might not be too difficult. But there is an easier way, especially for larger bibliographies where writing it out by hand may be very tedious. 

Many citation managers (software which allows you to easily save your sources) can automatically generate a .bib file which contains all the necessary information for LaTeX to be able to create your bibliography for you. Here we will show how this process works using a free, open-source citation manager called Zotero. This is not an in-depth look at how to use Zotero or any other citation manager, for more information about citation managers please check out these [guides](https://researchguides.library.brocku.ca/citationmanagement), the [Zotero documentation](https://www.zotero.org/support/) or keep an eye out on ExperienceBU to see when the Library is next holding their Zotero workshop. 

To export your Zotero library to a .bib file go to File > Export Library > select Format "BibTeX" > OK > Save the file in an appropriate location. 

Once you have your .bib file, press the upload button in the upper left of your Overleaf editor (the same one you used to upload your image) and upload the .bib file. 

Recompiling your document at this point won't have any effect. First we need to tell LaTeX where we are storing the bibliography information and what style we want the bibliography in by adding the following two commands at the end of our document (above `\end{document}`). 

```latex
\bibliographystyle{plain} %other styles are available
\bibliography{bibliography} % this should be whatever your file is named, here it is called "bibliography.bib"
```

If you recompile your document at this point, still not much will happen. Only items that you `\cite{}` in your document will appear in your bibliography. To cite an item you'll need to know what label it has (similar to when you use the label of a figure or table to `\ref{}` it). To find the label we'll look at the .bib file. 

An example of an entry in a .bib file would be 

```latex
@book{mittelbach2004latex,
  title={The LATEX companion},
  author={Mittelbach, Frank and Goossens, Michel and Braams, Johannes and Carlisle, David and Rowley, Chris},
  year={2004},
  publisher={Addison-Wesley Professional}
}
```

The label for this bib entry is "mittelbach2004latex", so to cite it we'd write `\cite{mittelbach2004latex}`. For example

```latex
There are many resources for learning more about LaTeX, including books like \cite{mittelbach2004latex}. 
```

[Various bibliography styles are available](https://www.overleaf.com/learn/latex/Bibtex_bibliography_styles) for use with BibTeX, and there is a lot more that we didn't cover here which you can find in the [Overleaf Help Documentation](https://www.overleaf.com/learn/latex/Bibliography_management_with_bibtex).

## Using templates

It is often helpful (and sometimes required) to use a template for your LaTeX document. We are going to look at a couple of ways to get templates into Overleaf and how to use them. 

### Using templates from Overleaf
When creating your project, Overleaf gives you the option to search for a template in their catalog. For this tutorial we'll look up the IEEE Conference Paper Template. 

Go to your Overleaf project page and press "New Project". Under the "Templates" section, press "View All". Then use the search bar to search for IEEE. Click on the link that says "IEEE Conference Template" and then select "Open As Template".

The template will open in the Overleaf editor. Note that it has already been filled with boilerplate text and content. This text can be helpful to look over as a reminder for how to add various types of content to your document. Additionally, it contains some helpful guidance on how to adhere to the IEEE specifications for conference papers. 

All the basic LaTeX commands and techniques we covered earlier still apply here. 

### Uploading templates from .zip

You may have to use a custom template for your document, often these will be provided to you as .zip files that you'll need to import into Overleaf to use. 

Here we are going to load the same IEEE conference template in again, this time from a .zip file. 

Firstly, we need to get the .zip file from the IEEE website [here](https://www.ieee.org/conferences/publishing/templates.html) by clicking on the "Template" link under the "LaTeX Template Instructions" subheading. (Note: the LaTeX Template Instructions document is a very thorough description of the IEEEtran LaTeX class and its usage, if you want to really dig more into how it works)

Once you have downloaded and saved the template, go back to the Overleaf projects page and select New Project > Upload Project, then drag in the .zip file. The template should open in the Overleaf editor, and you can use it just as before!

# Useful Resources + Further Reading

The [Overleaf help documentation](https://www.overleaf.com/learn) is a great reference for many common questions you may have about working with LaTeX. 

IEEE LaTeX templates can be found on Overleaf [here](https://www.overleaf.com/org/ieee).

BibTeX guides can be found [here](https://www.overleaf.com/learn/latex/Bibliography_management_with_bibtex) as well as a [video showing a minimal example for creating a bibliography](https://www.overleaf.com/learn/latex/Questions/How_to_include_a_bibliography_using_bibtex)

For more information on citation management software and Zotero, please see the following web pages. 

[Library Research Guides on Citation Management](https://researchguides.library.brocku.ca/citationmanagement)

[Zotero Documentation](https://www.zotero.org/support/)
