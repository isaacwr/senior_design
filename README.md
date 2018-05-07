Turquoise Blue
===============
Kalina Allen, Elena Cokova, Isaac Rothschild

What the project is about, who is it for?
-----------------------------------------
Jupyter is an open-source web application that allows users to create and share documents that contain live code, equations, visualizations and narrative text. Some of its main uses include: data cleaning and transformation, numerical simulation, statistical modeling, and data visualization. 

Jupyter projects are structured in the form a notebook made of a collection of cells. Each cell contains either documentation, runnable code, or the output of a code cell. This format offers the flexibility to rerun code on custom data as needed to support the analysis in the documentation sections. 

Our contribution to Jupyter is adding git-based revision control to notebooks to allow users to switch between notable snapshots.

What are the main software components?
--------------------------------------
The Jupyter Notebook Module, which handles all of the pre-existing notebook functionality. We added code to display a “create snapshot” button and “restore snapshot” list and to interface with the GitStoreServer module. 
The GitStoreServer, which handles POST requests from Jupyter notebook and calls the appropriate endpoints in the GitStore module.
The GitStore Module, which interacts with git to save changes and fetch old versions of a Jupyter Notebook. 

How do they work, how do they work together?
--------------------------------------------
We altered the following Jupyter notebook module components to interact with our GitStore module via HTTP POST requests.

- Menubar.js, for creating the the Create/Restore Snapshot UI, populating the list of snapshots, and restoring from an old snapshot.

- SaveWidget.js, for creating new snapshots and saving and renaming a notebook.

- NotebookList.js, for deleting existing notebooks.

- Notebook.js, for creating new notebooks.

Are there particular system requirements?
-----------------------------------------

Python 3  (needed for the git store server) - https://www.python.org/downloads/ 
    
Git 1.7 or higher - https://git-scm.com/ 

Pip - https://pip.pypa.io/en/stable/installing/ 

GitPython  - http://gitpython.readthedocs.io/en/stable/intro.html 

How to download, build, and run the system
------------------------------------------

Ensure that all system requirements are met before continuing. 

Fork our Jupyter notebook source from: https://github.com/kallen07/notebook 
        
Follow the instructions written CONTRIBUTING.rst (https://github.com/kallen07/notebook/blob/master/CONTRIBUTING.rst) to install components needed.
    
Go to a folder that does not contain an existing git repo, and start jupyter:
    
        jupyter notebook
        
From the source code directory, start the git store server:
    
        python3 tools/git_store_server.py 8000 [path_to_jupyter_notebook]
        
 Note: jupyter currently expects the git store server to be running on port 8000, despite the port being customizable for git_store_server.

Future work: things that need to be done, things that others could contribute in the future
--------------------------------------------------------------------------------------------
- Renaming and deleting snapshots

- Evaluating snapshots (color, thumbs up, etc)

- More information on snapshots (eg: timestamp)

- Integrate with git submodules so that we can create notebooks inside of existing git repos

- More interesting UI for interacting with all saves (eg: timeline you can scroll through)

- Integrating GitStoreServer with jupyter so that it is started immediately.

- Be able to specify the port of the GitStoreServer.

Sponsor
-------
This project is sponsored by Professor Alva Couch.


