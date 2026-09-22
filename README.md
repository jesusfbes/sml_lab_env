# Student Setup Guide

In this course, we will use Python in Jupyter notebooks. To keep setup consistent across computers, this repository uses an isolated environment containing the required libraries. You do not need previous Python experience to follow this guide.

## 1. Tools

- **Visual Studio Code (VS Code):** editor for opening and running notebooks.
- **uv:** installs and manages the Python environment and project libraries.
- **Jupyter:** runs `.ipynb` notebooks.

The repository only include the environment configuration. You do not need to install libraries individually. You do have to include the actual exercises inside the project.

## 2. Install Visual Studio Code

Download and install VS Code with the default options: <https://code.visualstudio.com/download>.

## 3. Install uv

### Windows

Open PowerShell and run:

```powershell
winget install --id=astral-sh.uv -e
```

Close and reopen PowerShell, then check the installation with `uv --version`.



### Linux / MACos

Open a terminal and run:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Close and reopen the terminal, then check the installation with `uv --version`.

## 4. Get the course repository

Download or clone this repository and save it somewhere easy to find, for example `Documents/sml_lab_env`. Avoid locations that cause permission problems or very long paths.


## 5. Open the project in VS Code

1. Open VS Code and select **File → Open Folder...**.
2. Choose the `sml_lab_env` project folder, not just an individual notebook.
3. Confirm the trust prompt if VS Code shows one for the course repository.

Opening the full folder lets VS Code find `pyproject.toml` and the project environment.

## 6. Install VS Code extensions

In the **Extensions** sidebar, install Microsoft's **Python** and **Jupyter** extensions.

## 7. Prepare the course environment

Open **Terminal → New Terminal** in VS Code. Make sure the terminal is in the project folder containing `pyproject.toml`, then run:

```bash
uv sync
```

The first setup can take a few minutes. It installs the Python version and project dependencies, including Jupyter, NumPy, pandas, Matplotlib, Seaborn, scikit-learn, and XGBoost. When it finishes, uv creates `.venv`, the isolated environment for this project.

Do not edit `.venv` manually or commit it to Git. If it is deleted, run `uv sync` again to recreate it.

## 8. Check the environment

Run these commands in the project terminal:

```bash
uv run python --version
uv run python -c "import numpy, pandas, sklearn, xgboost, matplotlib, seaborn; print('Environment ready')"
```

If the second command prints `Environment ready`, the libraries are available.

## 9. Include exercisesz in. the project

Download a laboratory exercise and put all the needed materials inside a folder inside `labs/`. E.g., `labs/lab01` for *lab01*. 

In VS Code's Explorer, open `labs/lab XX/` and then the notebook you want to use. Once the notebook is opened, at the top right, select **Select Kernel** and choose the project's `.venv` Python environment.

Run a cell by clicking its triangle button or selecting it and pressing **Shift + Enter**. Run cells from top to bottom because later cells may rely on variables created earlier.



## 10. Continue working another day

You do not need to repeat the installation. Open VS Code, open the `sml_lab_env` folder, open your notebook, and check that the `.venv` kernel is selected. If the instructor updates the project or provides a new `uv.lock`, run `uv sync`.

## 11. Common issues

### `uv` is not recognized

Close and reopen the terminal. If it is still unavailable, restart VS Code. On Windows, check `uv --version` in a new PowerShell window.

### `uv sync` cannot find the project

Make sure the terminal is in the folder containing `pyproject.toml` and `uv.lock`. Use `dir` in PowerShell or `ls` on macOS/Linux to check.


### `ModuleNotFoundError` appears

The notebook may be using another Python interpreter. Select the project's `.venv` kernel. Do not install libraries manually unless your instructor asks you to; a separate environment can make the notebook behave differently from the course setup.

### The notebook stops responding

Check the kernel status at the top of the notebook. If needed, select **Restart Kernel** and run the cells again from the beginning.

## 13. Working guidelines

- Do not delete `pyproject.toml` or `uv.lock`.
- Do not edit `.venv` manually.
- Do not run `pip install` unless your instructor asks you to.
- Run notebook cells in order when you start a session.
- Save your work in your own copy of a notebook.
- Do not put passwords, access keys, or personal information in notebooks.

## Quick reference

```text
Open VS Code
    ↓
Open the sml_lab_env folder
    ↓
Copy your exercise inside the project
    ↓
Open a notebook in your exercise
    ↓
Select the .venv kernel
    ↓
Run the cells
```

Update the environment if the project changes:

```bash
uv sync
```

Run JupyterLab in a browser:

```bash
uv run jupyter lab
```

## Need help?

If you still have problems, send your instructor your operating system, the command you ran, the complete error message, and a screenshot if useful. Include the full error text where possible; a partial screenshot may omit details needed to diagnose the issue.
