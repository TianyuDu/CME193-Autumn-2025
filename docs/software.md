# Software

**Pages:** [Course Description](index.md) · [Homework](homework.md) · [Local Jupyter](local-jupyter.md) · [Google Colab](google-colab.md) · [Software](software.md)

During the course, we will mainly be using Jupyter Notebook. Jupyter Notebooks can either be run locally (e.g., using Anaconda) or in the cloud (e.g., using Google Colab). We will be distributing the lecture materials as Google Colab notebooks, but you are welcome to download them and run them locally.

You can choose either way to run these notebooks depending on how much setup and installation you want to do on your local machine. We will be using Colab for live lectures to minimize the disruption due to local installation issues.

Please talk to the PI during office hour if you faced any challenges with the software.

# Python Version
We recommend using Python newer than 3.9 (including 3.9) for this course. We would recommend using Python 3.12.

# Running Notebooks in the Cloud (Colab)

Google Colab lets you run Jupyter notebooks in the cloud without installing Python locally. It is ideal for this course's live coding and homework. This guide covers launching notebooks, using GPUs, managing files, installing packages, and ensuring reproducibility.

## Quick Start
1.  Log in to your Google account.
2. (Optional) claim the free pro account for education to access more compute resources [here](https://blog.google/outreach-initiatives/education/colab-higher-education/)
3. Go through the offical tutorial of colab [here](https://colab.research.google.com/notebooks/intro.ipynb).
4. Open the shared Colab link from the [schedule](schedule.md) or [homework](homework.md) pages.
5. Click **Open in Playground** to make an editable copy.
6. Execute a cell with `Ctrl` + `Enter` (`Cmd` + `Enter` on macOS).
7. Add a new cell with the **+ Code** button or by pressing `B` while a cell is selected.
Colab saves your changes to Google Drive and requires no local installation.

You can find more details below.

## Launching Colab
- Open a shared link from the syllabus or homework page. It will open in Colab.
- If the notebook is view-only, click the dropdown next to the notebook title and choose **Open in Playground mode** or use **File → Save a copy in Drive** to make your own editable copy.
- Run a cell with `Ctrl+Enter` (`Cmd+Enter` on macOS). Run and advance with `Shift+Enter`.

### Open from GitHub
- Use **File → Open notebook → GitHub** and paste a repo or file URL.
- Alternatively, append a GitHub URL to Colab: `https://colab.research.google.com/github/<user>/<repo>/blob/<branch>/<path>.ipynb`.

## Runtimes, GPU/TPU, and Sessions
- Check current runtime type via **Runtime → Change runtime type**.
  - Hardware accelerator: None, GPU, or TPU.
  - Recommended for this course: GPU for deep learning content.
- Reset or restart via **Runtime → Restart runtime**.
- Colab sessions are ephemeral:
  - Idle timeout: typically ~90 minutes without execution.
  - Max session length: often 12 hours; GPU sessions may be shorter and quota-dependent.
  - Local files in `/content` vanish after the session ends; use Drive to persist.

## Installing Packages
Use `pip` inside a cell. Installs persist only for the session.

```bash
!pip -q install numpy pandas matplotlib scikit-learn torch torchvision
```

- If you have a `requirements.txt` (e.g., from homework), upload it or fetch it, then:

```bash
!pip -q install -r requirements.txt
```

- Prefer version pins for reproducibility (e.g., `numpy==1.26.4`).

## Files and Data
### Temporary workspace
- The working directory is `/content`. Anything saved here is temporary.

### Upload and download
- Upload small files via the left sidebar → Files → Upload, or programmatically:

```python
from google.colab import files
uploaded = files.upload()  # Prompts file picker
```

- Download a file you generated:

```python
from google.colab import files
files.download('results.csv')
```

### Mount Google Drive (persistent storage)
- Mount your Drive at `/content/drive`:

```python
from google.colab import drive
drive.mount('/content/drive')  # Follow the auth prompt
```

- Your files appear under `/content/drive/MyDrive/`. Example save/load:

```python
import pandas as pd
path = '/content/drive/MyDrive/cme193/data.csv'
df = pd.read_csv(path)
df.to_csv('/content/drive/MyDrive/cme193/output.csv', index=False)
```

### Download from the web or Drive (by link)
- Using `wget` or `curl` in a cell works well for public URLs:

```bash
!wget -q https://example.com/data.csv -O data.csv
```

- For Google Drive file IDs (publicly shared), use `gdown`:

```bash
!pip -q install gdown
!gdown 1A2B3C4D5E6F_example_drive_file_id -O data.csv
```

## Notebooks, Shortcuts, and UI Tips
- Insert cell below: `B`. Insert cell above: `A`.
- Delete cell: `D` then `D`.
- Interrupt execution: `Runtime → Interrupt execution` or stop button.
- Clear outputs: `Edit → Clear all outputs`.
- Variable inspector: use `%whos` in a cell to list variables.

## Reproducibility Best Practices
- Add a setup cell at the top of each notebook that installs and verifies versions:

```python
import sys, platform
print('Python', sys.version)
print('Platform', platform.platform())

import numpy as np, pandas as pd, sklearn
print('numpy', np.__version__)
print('pandas', pd.__version__)
print('scikit-learn', sklearn.__version__)
```

- Pin versions in `pip` installs to avoid surprises.
- Keep data in Drive and reference it via absolute paths.
- Rerun the setup cell after switching runtime types (e.g., enabling GPU).

## Using GPUs and PyTorch/TensorFlow
- After enabling GPU in runtime settings, verify availability:

```python
import torch
print('CUDA available:', torch.cuda.is_available())
print('Device count:', torch.cuda.device_count())
```

- Choose device in your code:

```python
device = 'cuda' if torch.cuda.is_available() else 'cpu'
```

- For TensorFlow 2, verify GPU:

```python
import tensorflow as tf
print(tf.config.list_physical_devices('GPU'))
```

## Connect to Local Runtime (optional)
You can run Colab’s front-end against your own machine’s Jupyter kernel.

1. Install Jupyter and the Colab Jupyter extension locally:
   ```bash
   pip install jupyterlab jupyter
   pip install jupyter_http_over_ws
   jupyter server extension enable --py jupyter_http_over_ws
   ```
2. Start a local server:
   ```bash
   jupyter notebook --NotebookApp.allow_origin='https://colab.research.google.com' --port=8888 --no-browser
   ```
3. In Colab: **Connect → Connect to local runtime** and enter `http://localhost:8888/`.

## Common Issues and Fixes
- Package missing after restart: Reinstall in the first cell or install from `requirements.txt`.
- Module version mismatch: Pin versions and restart runtime after install.
- Out-of-memory errors: Use a smaller batch size, reduce dataset size, or switch to a GPU runtime.
- FileNotFoundError: Confirm path under `/content` vs `/content/drive/MyDrive` after mounting.
- Permission errors on Drive: Ensure the file is in your Drive or shared with your account and that you have mounted Drive.
- If you hit GPU quota limits, switch to CPU for non-deep-learning exercises or try again later.


# Running Notebooks Locally
There are several ways to install Python locally, we recommend using conda. There are still two versions of conda, namely the Anaconda (comes with a GUI and preinstalled packages) and miniconda (barebone CLI tools). Please refer to the [Anaconda guide](https://www.anaconda.com/docs/getting-started/getting-started) for more details. You can choose either version depending on your preference. If you are not comfortable with the command line, we'd recommend using the Anaconda, which comes with a GUI called Anaconda Navigator.

## Anaconda (recommended and comes with a graphical user interface)
1. Install [Anaconda](https://www.anaconda.com) and choose the Python 3.12 distribution. This bundles Python, Jupyter Notebook, and common scientific packages.
2. Open Anaconda Navigator (found in your Start menu on Windows, or Applications on macOS). On the home screen, locate and click the "Launch" button under Jupyter Notebook.
3. From the Notebook Dashboard, navigate to the directory where you want to store your notebook.Click the "New" button on the right side and select the desired kernel (e.g., `Python 3.12`). This will open a new, untitled notebook in a new browser tab.
4. Click on "Untitled" at the top of the notebook to rename it.
5. Jupyter Notebooks are composed of cells. You can have:
   - Code Cells: For writing and executing code (e.g., Python).
   - Markdown Cells: For adding text, explanations, and formatting.
6. Executing Code: Type your code into a code cell and press Shift + Enter to execute it. The output will appear directly below the cell.
7. Saving: Notebooks are automatically saved periodically, but you can also manually save by clicking the "Save" icon or going to "File" > "Save and Checkpoint."
8. Sharing: Notebooks can be downloaded in various formats (e.g., .ipynb, HTML, PDF) for sharing.

## Miniconda (lightweight but requires command line interface)
1. Download Miniconda (Python 3.12) from the official site: https://docs.conda.io/en/latest/miniconda.html
2. Install Miniconda and open a new terminal (macOS/Linux) or Anaconda Prompt (Windows).
3. Create a clean environment for this course:
   ```bash
   conda create -n cme193 python=3.12 -y
   ```
4. Activate the environment:
   ```bash
   conda activate cme193
   ```
5. Install Jupyter and the IPython kernel into this environment:
   ```bash
   conda install -y jupyter ipykernel
   ```
6. (Optional but recommended) Register the kernel so it shows up in Jupyter as a named option:
   ```bash
   python -m ipykernel install --user --name cme193 --display-name "Python (cme193)"
   ```
7. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
   If a browser tab does not open, copy the `http://127.0.0.1:8888/...` or `localhost:8888` URL from the terminal into your browser (the port `8888` might be different if you have other services running on your machine).
8. In a notebook, select the kernel via **Kernel → Change kernel → Python (cme193)** if you registered it in step 6.


Need extra packages? Use `conda install <package>` or `pip install <package>` within your environment before relaunching the notebook server.