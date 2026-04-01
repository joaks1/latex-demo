# What is LaTeX?

[LaTeX](https://www.latex-project.org/)
is a markup language and document preparation system, used for typesetting
technical, scientific, and academic documents.
Unlike
What-You-See-Is-What-You-Get (WYSIWYG) editors, like Microsoft Word),
LaTeX separates content from formatting, allowing you to focus on writing
content while LaTeX handles complex formatting, mathematical formulas, and
bibliographies separately.

# Newer alternatives to LaTeX

The origins of LaTeX go all the way back to 1978, when computer scientist,
[Donald Knuth](https://en.wikipedia.org/wiki/Donald_Knuth),
first released TeX.
It's great, and I suspect it will continue to be used extensively for technical
and academic typesetting for many years to come.
But, there are some modern alternatives, like:

-   [Quarto](https://quarto.org/)
-   [Typst](https://typst.app/)
-   [Pandoc](https://pandoc.org/); Quarto is built on Pandoc

Personally, when starting new projects, I'm going to tryout Quarto.
Nonetheless, there's a good chance you will collaborate on projects that use
LaTeX, so let's learn the basics.

# Getting set up

## Get the files in this repo

If you have Git installed, the easiest way to get the files for the LaTeX demo
is to use the following command:

    git clone https://github.com/joaks1/latex-demo.git
    cd latex-demo

If you don't have Git,
here are some instructions to install it from a scripting class I teach (this is
optional; see below):

-   [Install Git](https://phyletica.org/teaching/s4b/setup/#2-git)


Alternatively, if you prefer not to use `git`, you can use `wget` or `curl`
from the command line to download the files in this repo.
To use `wget`:

    wget https://github.com/joaks1/latex-demo/archive/main.zip

To use `curl`:

    curl -L -O https://github.com/joaks1/latex-demo/archive/main.zip

After using one of the commands above, you should have `main.zip` downloaded.
Unzip `main.zip` and `cd` into the new `latex-demo-main` directory:

    unzip main.zip
    cd latex-demo-main

## Accessing LaTeX, Option 1: Use Overleaf

As an AU employee/student, you should have free access to a premium account.
Try this link to learn more:

-   <https://www.overleaf.com/edu/auburn#quick-start>

Once your account is setup and your on the landing page for your Overleaf account,
click "New project" and then "Blank project".

After your new project is created, you can use the up-arrow-upload button to
upload the `manuscript.tex` document from this repo that you downloaded above.

## Accessing LaTeX, Option 2: Tectonic

If you want to follow along with this demo locally (*i.e.*, not on Overleaf),
There are several options for installing a LaTeX typesetting system.
The "traditional" options include:

-   Installing [TexLive](https://www.tug.org/texlive/) for Linux users (or Windows too)
-   Installing [MikTex](https://miktex.org/) for Windows users
-   Installing [MacTex](https://www.tug.org/mactex/) for Mac users

[Tectonic](https://tectonic-typesetting.github.io) is a newer way that attempts
to make LaTeX easier to install and use..
Below, I describe how to either install Tectonic directly, or use it via a
Conda environment.

### Installing Tectonic directly

Go to the [Tectonic website](https://tectonic-typesetting.github.io) and
click the "Install" tab for instructions for how to install Tectonic on your
computer.

### Using Tectonic via Conda

If you don't have `conda` on your computer.
Here is some info about conda and instructions for installing conda-forge from
a scripting class that I teach:

-   [Conda-forge installation](https://phyletica.org/teaching/s4b/setup/#4-conda-package-manager)

I prefer to use micromamba, which works identically to conda. Here are
instructions for installing micromamba
(NOTE: Either conda-forge or micromamba are great; you don't need both):

-   [Installing micromamba](https://mamba.readthedocs.io/en/latest/installation/micromamba-installation.html)

Once you have conda (or micromamba) installed, open a terminal window and navigate to
`latex-demo` directory, for example:
    
    cd latex-demo

Then, use conda to create the environment specified in the `conda-env.yml` file
(NOTE: If you installed micromamba, just replace `conda` in the command below
with `micromamba`:

    conda env create --file conda-env.yml

It will ask you to confirm changes; just type `y` and hit return.

Once conda finishes, you can activate the new `latex-demo` conda environment
with the following command (again, if you're using micromamba, just replace
`conda` with `micromamba` below):

    conda activate latex-demo

You should now have access to all the tools you need to compile LaTeX
documents.

# The demo

## Our first LaTeX file

In this (`latex-demo`) directory, you will find a document called `manuscript.tex`.
Open `manuscript.tex` with your preferred text editor.
It should look like:

```latex
\documentclass{article}

\begin{document}

Hello, World!
This is my first \LaTeX{} document!

\end{document}
```

This is the simplest possible LaTeX document.
Everything before `\begin{document}` is called the preamble.
The preamble is where we specify most formatting stuff, like:

-   The type of document we want our LaTeX code to compile into; `article` in
    this case
-   Packages we want to load and use
-   Page layout, margins, font, etc.
-   Define macros we want to use in our document

In our current `manuscript.tex` file, we have the absolute minimum in the
preamble, so all of LaTeX's defaults for the `article` class will be used.

All of our content (text that will be in our compiled document) goes
between `\begin{document}` and and `\end{document}`.
Currently, we just have plain text in our document, except for one
macro (or command), `\LaTeX{}`. LaTeX provides a lot of macros we can use,
and we can create our own (more on this in a bit).

## Compiling `manuscript.tex` into a PDF

How we compile `manuscript.tex` into a PDF will depend on what software we are
using.

If you are using Overleaf, it might be setup to automatically compile whenever
you make edits to to `manuscript.tex`; you can also click the "Recompile"
button.

If you are using Tectonic, you can compile using the `tectonic` command-line
tool:

    tectonic manuscript.tex

If you are using TexLive, MikTex, MacTex you should be able to use the
`latexmk` command-line tool to compile:

    latexmk -pdf manuscript.tex

After compiling, you should have a new `manuscript.pdf` PDF file; open it up
and take look.

Notice that "Hello, World!" and "This is my first LaTeX document" are on the
same line in the PDF, despite being on different lines in the `.tex` file.
This is because LaTeX treats a block of text separated by, at most, one new
line character as a paragraph.

## Sentence and paragraph basics

Let's add some more content to experiment with how LaTeX differentiates
paragraphs:

```latex
\documentclass{article}

\begin{document}

Hello, World!
This is my first \LaTeX{} document!
I'm adding a third sentence to the first paragraph.

This should be the first sentence of a new paragraph.

\end{document}
```

Compile the `manuscript.tex` again and look at the updated `manuscript.pdf` PDF
file.
Notice, that adding 2 (or more) new lines creates a new paragraph.

Now, let's a bunch of spaces between "Hello," and "World!", and a bunch of new lines
between our first and second paragraph:

```latex
\begin{document}

Hello,                 World!
This is my first \LaTeX{} document!
I'm adding a third sentence to the first paragraph.




This should be the first sentence of a new paragraph.

\end{document}
```

Go ahead and compile, and notice that this does not change the PDF document at
all!

## Comments

Any text that begins with `%` are called comments, LaTeX ignores these when
compiling the document.
Let's try adding 2 comments:

```latex
\begin{document}

Hello,                 World!  % An end of line comment
This is my first \LaTeX{} document!
I'm adding a third sentence to the first paragraph.

% A thought I want to remember, but not appear in the document
This should be the first sentence of a new paragraph.

\end{document}
```

After compiling, notice, again, the PDF did not change.
Comments are **very** useful!
They make it very easy to remove text from the final document, but keep it in
the `.tex` file.
Comments also allow you to capture your thoughts throughout the `.tex` file,
without affecting the PDF.

## Bold, italics, etc.

LaTeX has a bunch of macros defined by default for doing simple formatting
things. Here are a few:

-   `\textbf{}`: Bold
-   `\textit{}`: Italics
-   `\underline{}`: Underline
-   `\emph{}`: Italicise if used in "normal" text; reverse to non-italics if
    used inside italicized text.

Let's try some of them out:

```latex
\begin{document}

Hello,                 World!  % An end of line comment
This is my \textbf{first} \LaTeX{} document!
I'm adding a \textit{third} sentence to the first paragraph.

% A thought I want to remember, but not appear in the document
This should be the \textbf{\textit{first}} sentence of a new paragraph.

\end{document}
```

## Quotations

In LaTeX we specify single and double quotes using
`` `...' ``
and
``` ``...'' ```
respectively.
For example, let's quote "paragaph" in our last line:

```latex
This should be the \textbf{\textit{first}} sentence of a new ``paragraph''.
```

Compile again, and voila!


## Math

One of LaTeX's greatest strengths is how easy it is to typeset math equations.

For "inline" math formatting, you can use `$...$` notation.
Let's try it:

```latex
\begin{document}

Hello,                 World!  % An end of line comment
This is my \textbf{first} \LaTeX{} document!
I'm adding a \textit{third} sentence to the first paragraph.

% A thought I want to remember, but not appear in the document
This should be the \textbf{\textit{first}} sentence of a new paragraph.

A third paragraph with the famous $E = mc^2$ equation.

\end{document}
```

For "display" math formatting we can use `\[ ... \]` for unnumbered equations,
or `\begin{equation} ... \end{equation}` for numbered equations.
Let's try:

```latex
\begin{document}

Hello,                 World!  % An end of line comment
This is my \textbf{first} \LaTeX{} document!
I'm adding a \textit{third} sentence to the first paragraph.

% A thought I want to remember, but not appear in the document
This should be the \textbf{\textit{first}} sentence of a new paragraph.

A third paragraph with the famous $E = mc^2$ equation.
When pondering
\begin{equation}
p(A | B) = \frac{ p(B | A) p(A) }{ p(B) },
\end{equation}
it's clear that science is a practice of conditional probabilities.

\end{document}
```


## Adding a title

To add a title to our document, we can use the `\title` macro in our preamble
to define the title, and then use the `\maketitle` macro to add the title to
our compiled document:

```latex
\documentclass{article}

\title{A witty, descriptive title for my manuscript}

\begin{document}

\maketitle

Hello,                 World!  % An end of line comment
This is my \textbf{first} \LaTeX{} document!
I'm adding a \textit{third} sentence to the first paragraph.

% A thought I want to remember, but not appear in the document
This should be the \textbf{\textit{first}} sentence of a new paragraph.

\end{document}
```

After compiling, you should see the title in the PDF file.
Notice, you will also see today's date;
`\maketitle` includes the current date by default.
We can specify a different data if we want:

```latex
\documentclass{article}

\title{A witty, descriptive title for my manuscript}
\date{March 31, 2026}
```

We can also remove the date, by defining it as empty:

```latex
\documentclass{article}

\title{A witty, descriptive title for my manuscript}
\date{}
```

## Adding authors and affiliations

Next, let's update our preamble to use the `authblk` package to add authors and
affiliations.
The `authblk` package is not necessary, but it does make assigning affiliations
to authors easier.

```latex
\documentclass{article}
\usepackage{authblk}

\title{A witty, descriptive title for my manuscript}
\date{}

\author[1,2]{Aubbie U. Phyletica}
\author[2]{War D. Eagle}
\author[1,3]{Fred Flintstone}
\affil[1]{Auburn Univeristy Museum of Natural History}
\affil[2]{Auburn Univeristy Department of Biological Science}
\affil[3]{The Pleistocene}
```

After compiling the document, notice that the numbers in the square brackets
determine how the affiliations are assigned to the authors.

## Adding images

Next, let's add a figure to our doc.



# Other resources

-   [Learn LaTeX in 30 minutes with Overleaf](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes)
-   [Overleaf's quick-start guide for AU](https://www.overleaf.com/edu/auburn#quick-start)
-   [LaTeX Tutorial: Discover the beauty of LaTeX](https://latex-tutorial.com/)
