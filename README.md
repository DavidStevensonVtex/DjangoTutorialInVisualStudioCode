# Django Tutorial InVisual Studio Code
[Django Tutorial in Visual Studio Code](https://code.visualstudio.com/docs/python/tutorial-django)

The completed code project from this Django tutorial can be found on GitHub: [python-sample-vscode-django-tutorial](https://github.com/microsoft/python-sample-vscode-django-tutorial).

If you have any problems, you can search for answers or ask a question on the [Python extension Discussions Q&A](https://github.com/microsoft/vscode-python/discussions/categories/q-a).

## Prerequisites

1. Install the [Python Extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python)

1. Install a version of Python 3.

1. On Windows, make sure the location of your Python interpreter is included in your PATH environment variable.

    (bash) echo $PATH | tr ":" "\n" | grep -i python

## Create a project environment for the Django tutorial

1. On your file system, create a project folder for this tutorial, such as hello_django.

1. In that folder, use the following command (as appropriate to your computer) to create a virtual environment named .venv based on your current interpreter:

    cd hello_django

    python -m venv .venv

1. Open the project folder in VS Code by running code ., or by running VS Code and using the File > Open Folder command.

1. In VS Code, open the Command Palette (View > Command Palette or (Ctrl+Shift+P)). Then select the Python: Select Interpreter command.

1. Run Terminal: Create New Terminal (Ctrl+Shift+`) from the Command Palette, which creates a terminal and automatically activates the virtual environment by running its activation script.

    Note: On Windows, if your default terminal type is PowerShell, you may see an error that it cannot run activate.ps1 because running scripts is disabled on the system. The error provides a link for information on how to allow scripts. Otherwise, use Terminal: Select Default Profile to set "Command Prompt" or "Git Bash" as your default instead.

1. Activate the Virtual Environment:

    cd hello_django

    source .venv/Scripts/activate

1. Install Django in the virtual environment by running the following command in the VS Code Terminal:

    python -m pip install django

    Files are installed to the .venv/Lib and .venv/Scripts folders. A .venv/pyenv.cfg file is created.

## Create and run a minimal Django app

### Create the Django project

1. In the VS Code Terminal where your virtual environment is activated, run the following command:

    django-admin startproject web_project .

    In the hello_django folder, the manage.py file is created. Other files are created under the .venv folder.

    A web_project folder is created with __init__.py, asgi.py, settings.py, urls.py and wsgi.py files.

    * __init__.py: an empty file that tells Python that this folder is a Python package.

    * asgi.py: an entry point for ASGI-compatible web servers to serve your project. You typically leave this file as-is as it provides the hooks for production web servers.

    * settings.py: contains settings for Django project, which you modify in the course of developing a web app.

    * urls.py: contains a table of contents for the Django project, which you also modify in the course of development.

    * wsgi.py: an entry point for WSGI-compatible web servers to serve your project. You typically leave this file as-is as it provides the hooks for production web servers.

1. Create an empty development database by running the following command:

    python manage.py migrate

    A db.sqlite3 file is created under the hello_django folder.