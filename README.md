# Python Environment Setup to Install pycaret
Guide for setting up Python on Windows 11 and install pycaret

## 1. Context
- Two years of experience with Python
- Experience with Data Analysis and Personal Product Development
- Adhoc Environment Setup based on various online articles (Problem)
- Installation failure of 'pycaret' made me aware of the importance of a structured approach
  
## 2. Goals
1. Creating a clean environment
2. Documenting the setup process of a virtual environment

## 3. Summary
### Adopt
- 'pyenv' for Python's version management
- 'poetry' for modules version management  
Merit: It is possible to convey this virtual environment to others with this method.
### Also, the following method is for novices, but I didn't explain about this here.
- 'pyenv' for Python's version management 
- 'venv' for modules version management  
Demerit: It is difficult to convey this virtual environment to others with this method.

---

## 4. Process Flow for the first time
### 4-1. Uninstall Anaconda
1. Open Anaconda Prompt using the Windows search
![anaconda prompt](https://github.com/user-attachments/assets/b5e0e885-e7c4-4d0b-8b02-438971892016)
2. Install anaconda-clean package
   `conda install anaconda-clean`
   When asked "Proceed([y]/n)?", enter y and press Enter.  
3. Conduct anaconda-clean
   `anaconda-clean --yes`  
   -- yes means to skip to be asked for confirmation of each module for uninstallation.
   Got a backup automatically like C:\Users\username\.anaconda_backup\2025-01-17T094734 
4. Open explore and delete anaconda3\envs folder and anaconda3\pkgs in user folder  (**Note:** The anaconda3 folder might be named anaconda in some formats.)
![delete files](https://github.com/user-attachments/assets/e2c4a377-d294-46a8-a1c1-2a431ce735fc)
5. Unistall anaconda
![uninstall anaconda](https://github.com/user-attachments/assets/9a7bb7a4-0bbb-41e7-b2b4-ae6d0b2ad4b1)

### 4-2. Check The Current State - python, pyenv, poetry
Checking the versions
- `python --version`
- `pyenv --version`
- `poetry --version`
![versions check](https://github.com/user-attachments/assets/24cd4872-f6ce-4285-a103-acd1a7ac7f8c)

### 4-3. Install pyenv
1. Launch Windows PowerShell as Administrator
2. Use `Set-ExecutionPolicy RemoteSigned`, to enable to install pyenv on Windows PowerShell normal mode
3. Open Windows PowerShell as the normal version
4. Use `Invoke-WebRequest -UseBasicParsing -Uri "https://raw.githubusercontent.com/pyenv-win/pyenv-win/master/pyenv-win/install-pyenv-win.ps1" -OutFile "./install-pyenv-win.ps1"; &"./install-pyenv-win.ps1"`
![install pyenv](https://github.com/user-attachments/assets/83d2654c-d447-46c5-b563-b40b78d228c4)
5. Use `pyenv install --list` to list installable Python versions
6. Use like `pyenv install 3.12.3` and `pyenv install 3.11.1` to install Python versions you need
7. Use `pyenv versions` to check all Python versions installed
8. Use `pyenv global 3.12.3` to specify Python version that you want to use
9. Use pyenv versions to check the Python versions used currently
10. Use `python --version` to check the Python versions used currently as well

### 4-4. Install poetry
1. Open PowerShell and run the following command to install Poetry: `(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | python -`
2. Configure the system Path by adding %APPDATA%\Python\Scripts as a new entry
3. Close and reopen PowerShell.
4. Verify the installation by running: `poetry -V` or `poetry --version`
5. Set the default to manage packages per project by running: `poetry config virtualenvs.in-project true`
6. Navigate to the project folder: `cd C:\Users\username\Desktop\environment_test`
9. Create a new Poetry project: `poetry new myproject`
10. Change into the newly created project directory: `cd myproject`
11. Save your source code in the myproject subdirectory
12. Run the following command in the parent project folder to generate the poetry.lock file: `poetry install`  
    **Note:** Do not manually edit the poetry.lock file, as it is managed by Poetry.
13. Install packages using Poetry: `poetry add numpy` and `poetry add requests==2.32.2`
14. Uninstall a package if needed: `poetry remove requests`
15. Key files managed by Poetry:  
**pyproject.toml:** Defines the required packages for the project. You can manually edit this file to update package versions (e.g., "numpy==2.2.1") and run `poetry update` to apply changes.  
**poetry.lock:** Stores the exact versions of installed packages. This file should not be manually edited.  
16. Enter the project’s virtual environment: `poetry shell`  
    **Note:** If this command fails, you need to install the poetry-plugin-shell plugin: `poetry self add poetry-plugin-shell`  
    For more information on enabling the poetry shell command:  
    Reddit discussion: https://www.reddit.com/r/learnpython/comments/1hxftvw/poetry_shell_the_command_shell_does_not_exist/  
    Plugin documentation: https://python-poetry.org/docs/cli/#script-project  
    Github Document: https://github.com/python-poetry/poetry-plugin-shell
17. To run your Python script, use the following command in the VS Code terminal in the virtual environment: `python myproject\script.py` (example)
18. Exit the virtual environment by running: `deactivate`

## 5. Process Flow to make a new project from the second time
1. Create a folder.
2. Enter the folder. And check the Python version currently used.: `pyenv versions` (If you want to change it, please do it now.)
3. Run `poetry new myproject` to create a new Poetry project.
4. Navigate to the project folder using `cd myproject` in the folder.  
   **Note:** Save your source code in the myproject subdirectory.
5. Run `poetry install` in the parent project folder to generate the poetry.lock file.
6. Go to the environment by runnig: `poetry shell`. **Note:** If impossible, use `poetry self add poetry-plugin-shell` first.
7. Install packages, such as numpy, by running `poetry add numpy` (this can also be done from the VS Code terminal).
8. Exit the virtual environment by running: `deactivate`  

**Frequently used prompts** 
| **Command**                     | **Example**                                | **Purpose**                                                                                   |
|----------------------------------|--------------------------------------------|-----------------------------------------------------------------------------------------------|
| **pyenv**                       |                                            |                                                                                               |
| `pyenv install --list`          | `pyenv install --list`                     | Lists all available Python versions.                                                         |
| `pyenv install [version]`       | `pyenv install 3.12.3`                     | Installs the specified Python version.                                                       |
| `pyenv versions`                | `pyenv versions`                           | Lists all installed Python versions.                                                         |
| `pyenv global [version]`        | `pyenv global 3.12.3`                      | Sets the specified Python version as the global default.                                      |
| `pyenv local [version]`         | `pyenv local 3.12.3`                       | Sets the specified Python version for the current project folder.                            |
| **poetry**                      |                                            |                                                                                               |
| `poetry new [project-name]`     | `poetry new myproject`                     | Creates a new Poetry project.                                                                |
| `poetry init`                   | `poetry init`                              | Initializes Poetry for an existing project.                                                  |
| `poetry install`                | `poetry install`                           | Installs dependencies and generates the `poetry.lock` file.                                   |
| `poetry shell`                  | `poetry shell`                             | Activates the virtual environment (must be run inside the project folder).                   |
| `poetry self add poetry-plugin-shell` | `poetry self add poetry-plugin-shell`    | Installs the shell plugin if `poetry shell` does not work.                                   |
| `poetry update`                 | `poetry update`                            | Updates packages based on the `pyproject.toml` file.                                         |
| `poetry add [package-name]`     | `poetry add numpy`                         | Adds a new package to the project.                                                           |
| `poetry remove [package-name]`  | `poetry remove numpy`                      | Removes a package from the project and updates pyproject.toml and poetry.lock.               | 
| `poetry env info`               | `poetry env info`                          | Displays basic information about the virtual environment.                                    |

**Frequently used package installation**
| **Command**                  | **Purpose**                                      |
|------------------------------|--------------------------------------------------|
| `poetry add pandas`          | Adds `pandas` to the project. Automatically installs `numpy` as a dependency. |
| `poetry add matplotlib`      | Adds `matplotlib` to the project.               |
| `poetry add seaborn`           | Adds `seaborn` to the project.                    |
| `poetry add requests`           | Adds `requests` to the project.                    |

## 6. How to Install PyCaret with Poetry in VSCode and Jupyter Notebook
**Note:** PyCaret and Poetry may not work well together, causing errors even with matching Python versions. Follow these steps to successfully install PyCaret using Poetry:
1. Install Python 3.9.13 using pyenv: `pyenv install 3.9.13` and `pyenv global 3.9.13`
2. Add kaleido to your project: `poetry add kaleido==0.2.1`
3. Manually edit the pyproject.toml file as follows (Yellow parts were changed):  
![tomlfile](https://github.com/user-attachments/assets/0d0d0d51-6e8f-4067-a2c7-6df27eb17aee)
4. Update the package installation and those versions based on the toml file: `poetry update`
5. Install the "Jupyter" extension in VSCode.
6. Create a Jupyter Notebook file (jupyter_notebook.ipynb) in the myproject subdirectory.
7. Add the ipykernel package to your virtual environment: `poetry add ipykernel`
8. Register the virtual environment as a Jupyter kernel: `poetry run python -m ipykernel install --user --name=your_env_name --display-name "Python (myproject-py3.9)"`
9. Restart VSCode
10. Select the kernel in VScode. Use the kernel selector in the top-right corner to choose your registered virtual environment.
11. Test PyCaret in jupyter_notebook.ipynb: `from pycaret.regression import *` If there are no errors, it means complete.

## Knowledge
- Don't use pip and conda at the same time. Both are version management tools, so they can confuse systems.
- It is not that virtual environments can use the packages in the base environment and supplement other required packages.
- It is common practice to list frequently used packages in a requirements.txt file and then install them all at once using *pip install -r requirements.txt*.
- pip: Pip Installs Packages (Python's standard package manager)
- The pip can be used after installing Python.
- If you uninstall Python, you no longer use pip.
- If you uninstall Python, pip will also be removed, or at least will no longer work.
- Even if the pip command remains on your system, it will not work because it does not have the Python to run it.
- Pycaret is supported with Python 3.9, 3.10 and 3.11. 

## Reference
- 初心者は何を使えばいい？【Pythonの仮想環境を比較】〜オススメを紹介 〜  
  English: What should I use for the Python Environment Creation.
https://www.youtube.com/watch?v=r4SkIhQThe0&t=31s  
- 【Mac大手術】ぐちゃぐちゃだったPythonの環境構築をやり直した話【さよならAnaconda】  
  English: How I rebuilt my messy Python environment  
https://qiita.com/A7_data/items/88e3f5f3428744ff3473
- Windows11でAnaconda（Python）を完全にアンインストールする方法  
  English: How to uninstall Anaconda with Windows11 completely.  
https://mochi-mochi-mochiko.com/windows11-anaconda-uninstall/#toc2
- Install pyenv-win  
https://github.com/pyenv-win/pyenv-win
- Install poetry  
https://python-poetry.org/docs/#installing-with-the-official-installer
- poetry shell problem  
https://www.reddit.com/r/learnpython/comments/1hxftvw/poetry_shell_the_command_shell_does_not_exist/
https://python-poetry.org/docs/cli/#script-project
https://github.com/python-poetry/poetry-plugin-shell
- 【Poetry】Poetryのチートシート  
  English: Poetry Cheat Sheet  
https://qiita.com/uchksh/items/b027a3200fd5171caeb8
- Windows 10 + Python + Poetry + pyenv-win の Visual Studio Code で Jupyter Notebook を利用  
  English: Use Jupyter Notebook with Windows10 + Python + Poetry + pyenv-win in VSCode  
https://qiita.com/kerobot/items/3726208cb13532b4d981
- VSCodeでJupyter Notebookを使ってみた【ゼロからPython勉強してみる】  
  English: How to use Notebook with VSCode
https://qiita.com/starfieldKt/items/ed7dee5142d9d5c177fd  
**--- The following articles are for the solution of using poetry and pycaret. ---**
- [ENH]: Poetry and Pycaret don't work together #3624  
https://github.com/pycaret/pycaret/issues/3624  
- Why can't I install a Python package with the Python requirement ">=3.8,<3.11" into a Poetry project with the Python version "^3.9"?  
https://stackoverflow.com/questions/73116647/why-cant-i-install-a-python-package-with-the-python-requirement-3-8-3-11-i  
- How to add kaleido package to poetry.lock file?  
https://stackoverflow.com/questions/70993385/how-to-add-kaleido-package-to-poetry-lock-file  
Writing your pyproject.toml  
https://packaging.python.org/en/latest/guides/writing-pyproject-toml/  
