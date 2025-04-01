Upgrade pip:

`python.exe -m pip install --upgrade pip`

Install virtualenv via pip:

`pip install virtualenv`

Test your installation:

`virtualenv --version`

## Basic Usage
1. Create a virtual environment for a project:

```Python
cd project_folder # change directory to project_folder (must exist in directory)
virtualenv venv # Create a folder in the current directory
```
Note: `virtualenv venv` will create a folder in the current directory which will contain the Python executable files, and a copy of the `pip` library which you can use to install other packages. The name of the virtual environment (in this case, it was `venv`) can be anything; omitting the name will place the files in the current directory instead.

