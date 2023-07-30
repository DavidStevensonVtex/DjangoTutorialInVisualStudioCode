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

    When you run the server the first time, it creates a default SQLite database in the file db.sqlite3 that is intended for development purposes, but can be used in production for low-volume web apps. For additional information about databases, see the [Types of databases](https://code.visualstudio.com/docs/python/tutorial-django#_types-of-databases) section.

1. To verify the Django project, make sure your virtual environment is activated, then start Django's development server using the command python manage.py runserver. The server runs on the default port 8000, and you see output like the following output in the terminal window:

    Watching for file changes with StatReloader

    Performing system checks...

    System check identified no issues (0 silenced).

    July 30, 2023 - 12:46:31

    Django version 4.2.3, using settings 'web_project.settings'

    Starting development server at http://127.0.0.1:8000/

    Quit the server with CTRL-BREAK.

1. When you're done, close the browser window and stop the server in VS Code using Ctrl+C as indicated in the terminal output window.

### Create a Django app

1. In the VS Code Terminal with your virtual environment activated, run the administrative utility's startapp command in your project folder (where manage.py resides):

    python manage.py startapp hello

    The command creates a folder called hello that contains a number of code files and one subfolder.

1. Modify hello/views.py to match the following code, which creates a single view for the app's home page:

    from django.http import HttpResponse

    def home(request):

        return HttpResponse("Hello, Django!")

1. Create a file, hello/urls.py

1. The web_project folder also contains a urls.py file, which is where URL routing is actually handled. 

1. Save all modified files.

1. In the VS Code Terminal, again with the virtual environment activated, run the development server with python manage.py runserver and open a browser to http://127.0.0.1:8000/ to see a page that renders "Hello, Django".

### Create a debugger launch profile

1. Switch to Run view in VS Code (using the left-side activity bar or F5). You may see the message "To customize Run and Debug create a launch.json file". This means that you don't yet have a launch.json file containing debug configurations. VS Code can create that for you if you click on the create a launch.json file link

1. Select the link and VS Code will prompt for a debug configuration. Select Python then Django from the dropdown and VS Code will populate a new launch.json file with a Django run configuration. The launch.json file contains a number of debugging configurations, each of which is a separate JSON object within the configuration array.

1. Scroll down to and examine the configuration with the name "Python: Django":

    The launch.json file should appear in Visual Studio Code.

    This configuration tells VS Code to run "${workspaceFolder}/manage.py" using the selected Python interpreter and the arguments in the args list. Launching the VS Code debugger with this configuration, then, is the same as running python manage.py runserver in the VS Code Terminal with your activated virtual environment. (You can add a port number like "5000" to args if desired.) The "django": true entry also tells VS Code to enable debugging of Django page templates, which you see later in this tutorial.

1. Test the configuration by selecting the Run > Start Debugging menu command, or selecting the green Start Debugging arrow next to the list (F5):

1. Ctrl+click the http://127.0.0.1:8000/ URL in the terminal output window to open the browser and see that the app is running properly.

1. Close the browser and stop the debugger when you're finished. To stop the debugger, use the Stop toolbar button (the red square) or the Run > Stop Debugging command (Shift+F5).

1. You can now use the Run > Start Debugging at any time to test the app, which also has the benefit of automatically saving all modified files.

### Explore the debugger