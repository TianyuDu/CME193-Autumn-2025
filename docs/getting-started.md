# Getting Started

**Pages:** [Course Description](index.md) · [Syllabus](syllabus.md) · [Homework](homework.md) · [Getting Started](getting-started.md) · [Local Jupyter](local-jupyter.md)

There are two supported workflows: run the provided notebooks in Google Colab (recommended for live lectures) or install Python locally so you can customize packages for research and future projects. We suggest setting up both so you can switch even when Colab is busy.

## Running Notebooks in the Cloud
- Open the shared Colab link from the [syllabus](syllabus.md) or [homework](homework.md) pages.  
- Click **Open in Playground** to make an editable copy.  
- Execute a cell with `Ctrl` + `Enter` (`Cmd` + `Enter` on macOS).  
- Add a new cell with the **+ Code** button or by pressing `B` while a cell is selected.  
Colab saves your changes to Google Drive and requires no local installation.

## Running Notebooks Locally
1. Install [Anaconda](https://www.anaconda.com) and choose the Python 3.9 distribution. This bundles Python, Jupyter Notebook, and common scientific packages.  
2. Verify your installation from Terminal (macOS/Linux) or Anaconda Prompt (Windows):
   ```bash
   python -V
   ```
   You should see a Python 3.9 version string.
3. Launch Jupyter Notebook from the same terminal:
   ```bash
   jupyter notebook
   ```
   The browser interface lets you navigate to `.ipynb` files and open them. If a browser tab does not appear automatically, copy the `http://` URL shown in the terminal and paste it into your browser.
4. Inside Jupyter, run cells with `Ctrl` + `Enter` (`Cmd` + `Enter` on macOS). Insert new cells via `B` or the menu item **Insert → Insert Cell Below**.

Need extra packages? Use `conda install <package>` or `pip install <package>` within your environment before relaunching the notebook server.
