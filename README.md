# test website

[Link to pages: https://jatic.pages.jatic.net/docs/test-website/](https://jatic.pages.jatic.net/docs/test-website/)

To view this website locally, do the following:
1. Install poetry through pip: `pip install poetry`
2. Install project dependencies through poetry: 
   1. Navigate to the project directory then enter: `poetry install --no-root` "`--no-root`" prevents a somewhat meaningless error that occurs because there are no python files in the repo.
      1. You can increase verbosity by adding -vvv (number of v's indicated level of verbosity) `poetry -vvv install --no-root`.
      2. If you have a hangup on Keyring, add to your bashrc `export PYTHON_KEYRING_BACKEND=keyring.backends.null.Keyring` and re-source your bashrc.
   2. Wait until installation completes
3. Choose of the following:
   1. Navigate to the project directory then enter: `poetry run mkdocs serve`
   2. Run mkdocs within the poetry environment
      1. Navigate to the project directory then enter: `poetry shell`
      2. `mkdocs serve`
4. Open the link in your browser (`http://127.0.0.1:8000/`)
