# My Python Notes

Where I keep my Python notes for starting projects

## Setting up pipenv

I've installed using `pip install pipenv`

Also importantly added `export PIPENV_VENV_IN_PROJECT=1` to my `.bash_profile`

### Installing Python things

- `brew install` will install at the system level. So `pyenv` (the python picker) was done this way
- `pip install` will install into the currently active pyenv python version. So pick this for global things per python version, like `pip install pipenv`.
- `pipenv install` will install dependencies into the current project. 

## Kicking off a project

### Make a git repo

- Start a git repo
- Add `.gitignore`
- cd into the project

### Get python project set up

- `pipenv install jupyterlab`
- `pipenv run jupyter lab`

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

### Jupter Lab uses wrong path

With Python 3.8 I couldn't Jupyter Lab to recognize the modules I install in the environment. It's not referencing the `kernel.json` file in the environment, but looks to a more global version instead.

Jupyter Notebook works, and Jupyter lab works in Python 3.7.7.







