# python-environment-setup
Guide for setting up Python on Windows 11

## 1. Context
- Two years of experience with Python
- Experience with Data Analysis and Personal Product Development
- Adhoc Environment Setup based on various online articles (Problem)
- Installation failure of 'pycaret' makes me aware of the importance of a structured approach

## 2. Goals
1. Creating a clean environment
2. Documenting the setup process of a virtual environment

## 3. Summary
### Adopt
- 'pyenv' for Python's version management
- 'poetry' for modules version management  
Merit: It is possible to convey this virtual environment to others with this method.
### Also, the following method is for novices
- 'pyenv' for Python's version management 
- 'venv' for modules version management  
Demerit: It is difficult to convey this virtual environment to others with this method.

### Procedure Flow
1. Uninstall Anaconda
2. 現状確認
3. 

## 4. Uninstall Anaconda
1. Open Anaconda Prompt using the Windows search
![anaconda prompt](https://github.com/user-attachments/assets/b5e0e885-e7c4-4d0b-8b02-438971892016)
3. Install anaconda-clean package
   `conda install anaconda-clean`
   When asked "Proceed([y]/n)?", enter y and press Enter.  
4. Conduct anaconda-clean
   `anaconda-clean --yes`  
   -- yes means to skip to be asked for confirmation of each module for uninstallation.
   Got a backup automatically like C:\Users\username\.anaconda_backup\2025-01-17T094734 
5. Open explore and delete anaconda3\envs folder and anaconda3\pkgs in user folder  (Note: The anaconda3 folder might be named anaconda in some formats.)
![delete files](https://github.com/user-attachments/assets/e2c4a377-d294-46a8-a1c1-2a431ce735fc)
6. Unistall anaconda
![uninstall anaconda](https://github.com/user-attachments/assets/9a7bb7a4-0bbb-41e7-b2b4-ae6d0b2ad4b1)


## 5. 現状確認 python, pyenv, poetry
- Checking versions
`python --version`
`pyenv --version`
`poetry --version`
![versions check](https://github.com/user-attachments/assets/24cd4872-f6ce-4285-a103-acd1a7ac7f8c)


## 6. Install pyenv
1. Launch Windows PowerShell as Administrator
2. Use `Set-ExecutionPolicy RemoteSigned`, to eable to install pyenv on Windows Powershell normal mode
3. Open Windows Powershell as normal version
4. Use `Invoke-WebRequest -UseBasicParsing -Uri "https://raw.githubusercontent.com/pyenv-win/pyenv-win/master/pyenv-win/install-pyenv-win.ps1" -OutFile "./install-pyenv-win.ps1"; &"./install-pyenv-win.ps1"`
![install pyenv](https://github.com/user-attachments/assets/83d2654c-d447-46c5-b563-b40b78d228c4)
5. Use `pyenv install --list` to list installable Python versions
6. Use like `pyenv install 3.12.3 and pyenv install 3.11.1` to install Python versions you need
7. Use `pyenv versions` to check all Python versions installed
8. Use `pyenv global 3.12.3` to specify Python version that you want to use
9. Use pyenv versions to check the Python versions used currently
10. Use `python --version` to check the Python versions used currently as well

## 7. Install poetry
Install the Python versions you need. For example:

1. Powershellで
2. (Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | python -
3. Pathの設定　%APPDATA%\Python\Scriptsを新規追加する。
4. Powershellをいったん閉じて再度起動する。
5. poetry -V　またはpoetry --versionでインストールできているか確認する。
6. poetry config virtualenvs.in-project trueでプロジェクトごとにpoetryでパッケージ管理することをデフォルトとする。
7. C:\Users\jinno\Desktop\environment_testに移動
8. poetry new myproject
9. cd myproject
10. サブディレクトリのmyprojectにソースコードを保存していく
11. プロジェクトフォルダー（親の方）の中でpoetry installすることでpoetry.lockを生成できる。poetry.lockは基本的に手動で書き換えない。
12. パッケージのインストール poetry add numpy
13. poetry add requests==2.32.2も試しにインストールしてみる
14. poetry remove requestsでuninstallもできる
pyproject.toml: 必要なパッケージの定義　poroject.tomlにて手動でバージョンを変更し、poetry updateでアップデートできる。"numpy==2.2.1"
poetry.lock: 実際にインストールされているパッケージ情報

15. poetry shellでこの環境内に入れる。　poetry self add poetry-plugin-shellでインストールしないとactivateできない。
16. https://www.reddit.com/r/learnpython/comments/1hxftvw/poetry_shell_the_command_shell_does_not_exist/　poetry shellは上記をしないと使えない
17. https://github.com/python-poetry/poetry-plugin-shell
18. deactivateでこの環境から抜け出せる。
19. poetry shellで入った状態でVS codeのターミナルからpython myproject\script.pyでnumpyを持ったpythonを動かせる。


なので、新しく環境を作る際は、
1. folder作成
2. poetry new myproject
3. cd myproject
4. サブディレクトリのmyprojectにソースコードを保存していく
5. プロジェクトフォルダー（親の方）の中でpoetry installすることでpoetry.lockを生成できる
6. パッケージのインストール poetry add numpy　（VSコードのターミナルからできる。）
7. poetry remove numpyでアンインストール
8. 



## Note
Don't use pip and conda at the same time. Both are version management tools, so they can confuse systems.
- It is not that virtual environments can use the packages in the base environment and supplement other required packages.
- It is common practice to list frequently used packages in a requirements.txt file and then install them all at once using *pip install -r requirements.txt*.


## Knowledge
- pip: Pip Installs Packages (Python's standard package manager)
- The pip can be used after installing Python.
- If you uninstall Python, you no longer use pip.
- If you uninstall Python, pip will also be removed, or at least will no longer work.
- Even if the pip command remains on your system, it will not work because it does not have the Python to run it.

## 懸念点
- もしかしたらpipでインストールしたもの全てを削除してからpythonをuninstallしないといけない。

## Reference
- 初心者は何を使えばいい？【Pythonの仮想環境を比較】〜オススメを紹介 〜  
https://www.youtube.com/watch?v=r4SkIhQThe0&t=31s  
- 【Mac大手術】ぐちゃぐちゃだったPythonの環境構築をやり直した話【さよならAnaconda】
https://qiita.com/A7_data/items/88e3f5f3428744ff3473
- Windows11でAnaconda（Python）を完全にアンインストールする方法
https://mochi-mochi-mochiko.com/windows11-anaconda-uninstall/#toc2

https://github.com/pyenv-win/pyenv-win

https://python-poetry.org/docs/#installing-with-the-official-installer

