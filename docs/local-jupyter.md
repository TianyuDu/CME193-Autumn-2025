# Local Jupyter

**Pages:** [Course Description](index.md) · [Syllabus](syllabus.md) · [Homework](homework.md) · [Getting Started](getting-started.md) · [Local Jupyter](local-jupyter.md)

_All commands on this page run from a terminal (bash/zsh/PowerShell), not inside the Python REPL._

## Jupyter Notebooks
[Jupyter](https://jupyter.org/) mixes executable code and rich Markdown in one document. Although Anaconda installs Jupyter automatically, you can add it to any Python distribution with `pip`:

```bash
pip install jupyter
```

Jupyter itself is not the Python interpreter; it launches kernels that run your code. You can use those kernels for Python or other languages that expose a Jupyter-compatible interface.

## Launching Jupyter
After installing the package, start a notebook server from the folder that holds your notebooks (or navigate there once the interface opens):

```bash
jupyter notebook
```

This command starts a local server and should open a browser tab automatically. Navigate to your `.ipynb` file and click to launch it. If the browser does not open, copy the printed `http://127.0.0.1:8888/...` URL into your address bar. Even if you use the Anaconda Launcher, practice running the command manually so you are comfortable working from terminals and remote machines.

## Conda Environments inside Jupyter
You only need to install Jupyter once, but each conda environment that you want to use in notebooks must expose its own kernel. From your base environment run:

```bash
conda install nb_conda
```

Then activate the environment you want to register (replace `cme193` with your environment name) and install an IPython kernel:

```bash
conda activate cme193
conda install ipykernel
```

The next time you launch Jupyter—even without the environment activated—you can pick `Python [conda env:cme193]` from the **Kernel → Change kernel** menu.
