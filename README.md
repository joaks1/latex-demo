# Getting set up

## Get the files in this repo

If you have Git installed, the easiest way to get the files for the LaTeX demo
is to use the following command:

    git clone https://github.com/joaks1/latex-demo.git

## Accessing LaTeX, Option 1: Use Overleaf

As an AU employee/student, you should have free access to a premium account.
Try this link to learn more:

-   <https://www.overleaf.com/edu/auburn#quick-start>

Once your account is setup and your on the landing page for your Overleaf account,
click "New project" and then "Blank project".

## Accessing LaTeX, Option 2: Using Conda

### Installing Conda

If you want to follow along with this demo locally (*i.e.*, not on Overleaf),
the easiest way to LaTeX up and running on your computer is to create a `conda`
environment with the `texlive-core` package installed.

Here is some info about conda and instructions for installing conda-forge from
a scripting class that I teach:

-   [Conda installation](https://phyletica.org/teaching/s4b/setup/#4-conda-package-manager)

I prefer to use micromamba, which works identically to conda.
Here are instructions for intalling micromamba:

-   [Installing micromamba](https://mamba.readthedocs.io/en/latest/installation/micromamba-installation.html)

### Creating the conda environment

Once you have conda installed, open a terminal window and navigate to
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

### Installing Git (optional)

If you want to be able to clone this repo, you will need to have Git installed.
Here are some Git installation insructions from a scripting class I teach:

-   [Install Git](https://phyletica.org/teaching/s4b/setup/#2-git)

# Other resources

-   [Learn LaTeX in 30 minutes with Overleaf](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes)
-   [Overleaf's quick-start guide for AU](https://www.overleaf.com/edu/auburn#quick-start)
-   [LaTeX Tutorial: Discover the beauty of LaTeX](https://latex-tutorial.com/)
