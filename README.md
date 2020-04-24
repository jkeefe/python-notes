# My Python Notes

Where I keep my Python notes for starting projects

## Kicking off a project

### Make a git repo

- Start a git repo
- Add `.gitignore`
- cd into the project

### Get python project set up

- `conda deactivate` (until I get rid of conda as a default)
- `pipenv install`
- `pipenv install jupyterlab`
- `pipenv run jupyter lab`

_NOTE: if you run into lock problems with pipenv, try adding `--skip-lock`_

### Using dotenv for environments

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
