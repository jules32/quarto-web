---
title: GFM
format: html
---

## Overview

While markdown is the input format for Quarto, it can also in some cases be an output format (for example, if you have a website or CMS that accepts markdown as input and want to incorporate computations from Python or R).

This article covers using Quarto to generate [GitHub Flavored Markdown](https://github.github.com/gfm/) (GFM). You might want to do this in order to:

-   Generate a GitHub README.md from a Jupyter notebook

-   Create pages for a GitHub wiki that include computations (e.g. plot output).

## GFM Format

Use the `gfm` format to create GitHub Flavored Markdown from Quarto. For example:

``` {.yaml}
---
title: "My Project"
format: gfm
---
```

To create a `README.md` using Quarto, start with a notebook (.ipynb) or computational markdown file (.qmd or .Rmd) that has README as it's file name stem, for example:

**README.qmd**

```` {.python}
---
title: "My Project"
format: gfm
jupyter: python3
---

This is a GitHub README that has content dynamically generated from Python:
  
```{python}
1 + 1
```
````

Render the README with:

``` {.bash}
$ quarto render README.qmd
```

Which will create `README.md` alongside your input file.

## GitHub Wikis

If you want to use Quarto to incorporate computations into a GitHub wiki start by [cloning the wiki for local editing](https://docs.github.com/en/communities/documenting-your-project-with-wikis/adding-or-editing-wiki-pages#adding-or-editing-wiki-pages-locally).

Then, simply create a computational markdown file (.ipynb, .qmd, .Rmd) for each page in the wiki. You can render all of these files at once into their corresponding .md files using [Quarto Projects](../getting-started/quarto-projects.md). For example:

``` {.bash}
$ quarto render
```

You don't even strictly need a Quarto project file to do this as `quarto render` will render all input files in a directory by default if there is no project file.
