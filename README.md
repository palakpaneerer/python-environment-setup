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

## 4. Uninstall Anaconda
1. Open Anaconda Prompt using the Windows search
![image](https://github.com/user-attachments/assets/c9ae0bd4-851b-4e0a-9a86-302366277327)
![anaconda prompt](https://github.com/user-attachments/assets/b5e0e885-e7c4-4d0b-8b02-438971892016)

3. Install anaconda-clean package
   `conda install anaconda-clean`
   When asked "Proceed([y]/n)?", enter y and press Enter.  
4. Conduct anaconda-clean
   `anaconda-clean --yes`  
   -- yes means to skip to be asked for confirmation of each module for uninstallation.
   Got a backup automatically like C:\Users\username\.anaconda_backup\2025-01-17T094734 
5. Open explore and delete anaconda3\envs folder and anaconda3\pkgs in user folder
![image](https://github.com/user-attachments/assets/524538e7-afe8-49c5-9663-1d59d392664b)


6. 
7. エクスプローラーを開き、ユーザーフォルダ内の環境フォルダ（anaconda3\envs）とパッケージフォルダ（anaconda3\pkgs）を削除します。
![image](https://github.com/user-attachments/assets/c6c98b63-5a34-4b8c-af62-8a91eceda493)



## Note
- Don't use pip and conda at the same time. Both are version management tools. So systems will have confusion.

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


