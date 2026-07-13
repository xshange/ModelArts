---
title: python在线机器下载安装包及依赖包，离线机器安装扩展包
short_title: python在线机器下载安装包及依赖包，离线机器安装扩展包
subject: Who
subtitle: python在线机器下载安装包及依赖包，离线机器安装扩展包
description: python在线机器下载安装包及依赖包，离线机器安装扩展包
---


##  下载安装包及依赖包🚀

From [the quick start tutorial](../get-started/index.md), you should already have created a `myst.yml` configuration file that is required to render your project.
To confirm this, run a Jupyter Book server to serve the quick start content:

🛠 Run `jupyter book start` to serve your quickstart content

```shell
$ cd mystmd-quickstart
$ jupyter book start
📖 Built README.md in 33 ms.
📖 Built 01-paper.md in 30 ms.
📖 Built 02-notebook.ipynb in 6.94 ms.
📚 Built 3 pages for myst in 76 ms.

      ✨✨✨  Starting Book Theme  ✨✨✨

⚡️ Compiled in 510ms.

🔌 Server started on port 3000!  🥳 🎉

      👉  http://localhost:3000  👈
```

🛠 Open your web browser to `http://localhost:3000`[^open-port]

[^open-port]: If port `3000` is in use on your machine, an open port will be used instead, follow the link provided in the terminal.

## Install the packages needed for execution

:::{note}
This section requires the `pip` command. It should normally be installed with Python.
:::

To execute the content in the `myst-quickstart` site, we must ensure that the proper environment is installed.
To do so, install the packages listed in `myst-quickstart/requirements.txt`.

🛠 Use `pip` to install the packages for executing

```shell
$ pip install -r requirements.txt
```

## Execute demo content at build time

Note that the content in `02-notebook/` has no outputs.
By default, Jupyter Book will not execute any notebooks when your site builds.
To execute your content at build time, use the `--execute` flag.

🛠 Execute your content and build your MyST docs

```shell
$ jupyter book start --execute
```

This will **execute** your notebook file before spinning up your Jupyter Book server.
Go back to `02-notebook/` and you'll see the outputs there.

:::{seealso}
For more information about executing notebooks, see [](xref:guide/execute-notebooks).
:::

## Label, reference, and embed an output

You can attach labels to notebook outputs so that you can reference them later on in your site.
MyST uses a special comment syntax for attaching metadata to Jupyter Notebook cells.
Each of them use comments (`#` in Python) and the **pipe operator** (`|`) to add metadata.

For example, this content would assign the label `mylabel` to the cell output:

```python
#| label: mylabel
print("hi")
```

Your quickstart notebook already defines a cell output in one of its cells, find it to experiment with this feature.

🛠 Find the cell that defines a label with the following code:

```python
#| label: horsepower
points & bars
```

This assigns the label `horsepower` to the output of that code cell.

You can reference it and embed it like you would any other item in MyST Markdown.

🛠 Add a reference to this cell, as well as an embedding in a figure by copy and pasting this into a markdown block of the notebook.

```markdown
Here we reference [](#horsepower).

And below we embed it:

![](#horsepower)
```

:::{seealso}
For more information about embedding notebook outputs, see [](xref:guide/reuse-jupyter-outputs).
:::

## Add an executable cell to your Markdown file

You can add any executable content to a MyST Markdown file.
This is useful if you want to more natively version control your executable content in a system like `git`.

To add executable content, use the `code-cell` directive.
This will tell Jupyter Book to execute anything inside.

🛠 Add the following code cell directive to `01-paper.md`

````
```{code-cell}
:label: markdown-myst
print("Here's some python!")
```

And here I reference [](#markdown-myst).
````

If you re-build your Jupyter Book site with `--execute`, the cell will be executed.
Notice how we've also added a **label** to the code block, but using the directive option rather than the Python comments syntax we used above.

:::{seealso}
For more information about writing computational content in Markdown, see [](xref:guide/notebooks-with-markdown).
:::

## Conclusion 🥳

That's it for this quickstart tutorial!
You've just learned how to add computational materials and execute your MyST Markdown document!
