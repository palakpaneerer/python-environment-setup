# Python Environment Setup
Guide for setting up Python on Windows 11

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

### Process Menu
#### --- Process Flow for the first time (Chapter 4) ---
4-1. Uninstall Anaconda  
4-2. Check the current state  
4-3. Install pyenv  
4-4. Install poetry  

#### --- Process Flow to make a new project from the second time (Chapter 5) ---

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
4. Open explore and delete anaconda3\envs folder and anaconda3\pkgs in user folder  (Note: The anaconda3 folder might be named anaconda in some formats.)
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
    Note: Do not manually edit the poetry.lock file, as it is managed by Poetry.
13. Install packages using Poetry: `poetry add numpy` and `poetry add requests==2.32.2`
14. Uninstall a package if needed: `poetry remove requests`
15. Key files managed by Poetry:  
pyproject.toml: Defines the required packages for the project. You can manually edit this file to update package versions (e.g., "numpy==2.2.1") and run `poetry update` to apply changes.  
poetry.lock: Stores the exact versions of installed packages. This file should not be manually edited.  
16. Enter the project’s virtual environment: `poetry shell`  
    Note: If this command fails, you need to install the poetry-plugin-shell plugin: `poetry self add poetry-plugin-shell`  
    For more information on enabling the poetry shell command:  
    Reddit discussion: https://www.reddit.com/r/learnpython/comments/1hxftvw/poetry_shell_the_command_shell_does_not_exist/  
    Plugin documentation: https://python-poetry.org/docs/cli/#script-project  
    Github Document: https://github.com/python-poetry/poetry-plugin-shell
17. To run your Python script, use the following command in the VS Code terminal in the virtual environment: `python myproject\script.py` (example)
18. Exit the virtual environment by running: `deactivate`

## 5. Process Flow to make a new project from the second time
1. Create a folder.
2. Run `poetry new myproject` to create a new Poetry project.
3. Navigate to the project folder using `cd myproject`.
4. Save your source code in the myproject subdirectory.
5. Run `poetry install` in the parent project folder to generate the poetry.lock file.
6. Go to the environment by runnig: `poetry shell`. Note: If impossible, use `poetry self add poetry-plugin-shell` first.
7. Install packages, such as numpy, by running `poetry add numpy` (this can also be done from the VS Code terminal).
8. Exit the virtual environment by running: `deactivate`  

| **Command**                     | **Example**                                | **Purpose**                                                                                   |
|----------------------------------|--------------------------------------------|-----------------------------------------------------------------------------------------------|
| **pyenv**                       |                                            |                                                                                               |
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
| `poetry env info`               | `poetry env info`                          | Displays basic information about the virtual environment.                                    |


## Knowledge
- Don't use pip and conda at the same time. Both are version management tools, so they can confuse systems.
- It is not that virtual environments can use the packages in the base environment and supplement other required packages.
- It is common practice to list frequently used packages in a requirements.txt file and then install them all at once using *pip install -r requirements.txt*.
- pip: Pip Installs Packages (Python's standard package manager)
- The pip can be used after installing Python.
- If you uninstall Python, you no longer use pip.
- If you uninstall Python, pip will also be removed, or at least will no longer work.
- Even if the pip command remains on your system, it will not work because it does not have the Python to run it.

## Reference
- 初心者は何を使えばいい？【Pythonの仮想環境を比較】〜オススメを紹介 〜  
https://www.youtube.com/watch?v=r4SkIhQThe0&t=31s  
- 【Mac大手術】ぐちゃぐちゃだったPythonの環境構築をやり直した話【さよならAnaconda】  
https://qiita.com/A7_data/items/88e3f5f3428744ff3473
- Windows11でAnaconda（Python）を完全にアンインストールする方法  
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
https://qiita.com/uchksh/items/b027a3200fd5171caeb8
