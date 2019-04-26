# Tesla Alfred Workflow
A workflow for interacting with a Tesla vehicle via the unofficial Tesla JSON API

## Screenshot
![Workflow in Action](workflow.gif)

## Requirements
* [Alfred 3](https://www.alfredapp.com)
* [Alfred 3 Powerpack](https://www.alfredapp.com/powerpack/) (paid upgrade — it's worth it!)

## Installation
* Download the [latest github release](https://github.com/ejsuncy/tesla-alfred-workflow/releases/latest) and open it with Alfred

## Software Updates
* This workflow auto-updates to the latest release by checking the repository once daily and prompting the user to install the update.
* You can also force update with magic argument: `tesla workflow:update`

## Usage
* The keywords for Tesla Alfred Workflow are: `tesla` and `tesla-activate`
  * `tesla-activate` to set one of your Tesla vehicles as the active one to use with this workflow
  * `tesla` to interact with the active vehicle

## Development
After changing the source files and/or snippet files, you'll need to export the project as a .alfred3workflow file.

I've included in this repository a modified gist from [here](https://gist.github.com/deanishe/b16f018119ef3fe951af) to build and export the workflow ([workflow-build.py](workflow-build.py)).
It includes dependencies that you'll need to install. Here's a recommended workflow:
* `virtualenv ~/.envs/workflow-build` creates a virtual environment so you can install the dependencies in their own sandbox
* `source ~/.envs/workflow-build/bin/activate` activates the virtual environment
* `cd tesla-alfred-workflow` moves you to the repo directory
* `pip install -r requirements.txt` installs the dependencies in this sandbox (leaving your global/system python alone)
* `python workflow-build.py -o output_dir .` exports the current repo directory as a .alfred3workflow file, excluding the following patterns:

|EXCLUDE PATTERNS|
|---|
|\*.pyc|
|\*.log|
|.DS_Store|
|\*.acorn|
|\*.swp|
|\*.sublime-project|
|\*.sublime-workflow|
|\*.git|
|\*.dist-info|
|\*.egg-info|
|\*.gif|
|README.md|
|workflow-build.py|
|requirements.txt|
|\*.idea|

You can add more patterns in the [workflow-build.py file](workflow-build.py) to exclude new file types that you don't want packaged in the zip file.

 

## Release Notes
### `v.0.0.8`
* Handle Unauthorized api response to prompt user to try resetting Tesla credentials.
### `v0.0.7`
* Update teslajson library to support polling API commands, resolves issue where sending API command raises ContinuePollingException
### `v0.0.1`
* Initial release

