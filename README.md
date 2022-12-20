# My Python Notes

Where I keep my Python notes for starting projects

## Installing Python things

- `brew install` will install at the system level. So `pyenv` (the python picker) was done this way
- `pip install` will install into the currently active pyenv python version. So pick this for global things per python version, like `pip install pipenv`.  
- `pipenv install` will install dependencies into the current project. 

## Setting up pyenv

I use `pyenv` to manage the operating Python version. 

### Mac install

Carefully follow the prerequisites and numbered steps in the [Mac install](https://github.com/pyenv/pyenv#homebrew-on-macos), which starts by using Homebrew.

Then add any requisite lines to the `.bashrc` file or `.zprofile` file (it will tell you what to add).

Note that you'll need to restart the shell to make it all work.

### Ubuntu install

Do the [Ubuntu install](https://github.com/pyenv/pyenv-installer) using auto-installer.

On Ubuntu 18.04, before doing the below to install Python 3.7, need to do the [following](https://code.luasoftware.com/tutorials/linux/ubuntu-pyenv-build-python-37-common-error/):

```
sudo apt-get update
sudo apt-get install build-essential libffi-dev libssl-dev libbz2-dev libreadline-dev libsqlite3-dev
```

### Using pyenv

```
pyenv install 3.7.8
pyenv global 3.7.8
pyenv versions
```

## Setting up pipenv

I use `pipenv` to manage the dependencies for each project. I prefer to keep those dependencies in the project folder, which these steps allow.

I've installed using `pip3 install pipenv`

Also importantly added `export PIPENV_VENV_IN_PROJECT=1` to my `.bash_profile`


## Kicking off a project

### Make a git repo

- Start a git repo
- Add `.gitignore`
- cd into the project

### Get python project set up

- `pipenv install jupyterlab`
- `pipenv run jupyter lab`

or, if not using Jupyter, jut:

- `pipenv install`

_NOTE: if you run into lock problems with pipenv, try adding `--skip-lock`_

### Using dotenv for environments

*NOTE:  Jupyter notebook and lab both take in the variables from a .env file if it exists, so the below is not needed.*

```bash
pipenv install python-dotenv
```
Then...

```python
from dotenv import load_dotenv
import os
load_dotenv()

DATABASE_PASSWORD = os.getenv("DATABASE_PASSWORD")
```

Just don't use spaces in the `.env` file. So:

```bash
DATABASE_PASSWORD=`sekrit`
```

## Various adventures and adjustments

### Pandas Error: Could not import the lzma module

```
Could not import the lzma module. Your installed Python is incomplete. Attempting to use lzma compression will result in a RuntimeError.
```

I got this from early on with my fresh python install. Looked up the fix and [found this](https://github.com/pandas-dev/pandas/issues/27532#issuecomment-517259553):


- `pip freeze > latestPackages.txt`
- `pyenv uninstall 3.7.3`
- `brew install xz` (This is how you pick up the correct lzma macOS)
- `pyenv install 3.7.3`

The brew command said that `xz` was already installed and up to date. So maybe it wasn't when I first installed python?

### Jupter Lab uses wrong path

With Python 3.8 I couldn't Jupyter Lab to recognize the modules I install in the environment. It's not referencing the `kernel.json` file in the environment, but looks to a more global version instead.

Jupyter Notebook works, and Jupyter lab works in Python 3.7.7.







