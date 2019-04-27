# Knowledge

Collecting thoughts in [index.md](index.md) with vimwiki and Jupyer notebooks


## Run a notebook remotely for reference ##

1. Enter details of a notebook in a public repo into [binder](https://mybinder.org/)

    
    For example: https://github.com/jonwhittlestone/knowledge
    
2. Or just click here<br>
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/jonwhittlestone/knowledge/master)


## Running the notebooks locally

1. Start a python3 virtual environment

    `virtualenv -p python3 venv; source venv/bin/activate`

2. Install jupyter notebook with pip

    `pip install jupyter`

3. Ensure you've globally installed the node plugin,`ijavascript`

    `npm install -g ijavascript`

4. Install the plugin

    `ijsinstall`
    
5. Start Jupyter notebook

    `jupyter notebook`
    
6. (Optional) Run in [Jupyer lab](https://jupyterlab.readthedocs.io/en/stable/)

    `pip install jupyterlab; jupyter lab`
    


## Running the notebooks

1. Start a python3 virtual environment

    `virtualenv -p python3 venv; source venv/bin/activate`

2. Install jupyter notebook with pip

    `pip install jupyter`

3. Ensure you've globally installed the node plugin,`ijavascript`

    `npm install -g ijavascript`

4. Install the plugin

    `ijsinstall`
    
5. Start Jupyter notebook

    `jupyter notebook`

## Dev-todos on Chrome Start Page

To give the Toodos a bit more visibility, out of Vim, the dev-todos page can be set as a Chrome Start page

![Chrome on macos Screenshot](images/dev_todos_browser.png)

Steps to do this in macos

1. Clone this repo
2. Ensure there is a dev-todos.md file
    mv dev-todos.md.example dev-todos.md
3. Move the launchd script to the Mac's daemon directory
    mv browsertab-wiki/init/macos/Library/LaunchAgents/com.browsertabwikiserver.plist /Users/jon/Library/LaunchAgents
4. Load the daemon
    launchctl load ~/Library/LaunchAgents/com.browsertabwikiserver.plist
5. You should see the page rendered by pointing your browser at http://localhost:2000
6. Install Replace New Tab Page Chrome extension
    https://chrome.google.com/webstore/detail/replace-new-tab-page/cnkhddihkmmiiclaipbaaelfojkmlkja
