# internal-docs

Please view on pages at [https://jatic.pages.jatic.net/internal-docs/](https://jatic.pages.jatic.net/internal-docs/)!

---

This project is the central location for all internal documentation within the JATIC program! It contains helpful guides, resources, and references aimed at the program's internal teams.

The aim of this project is to create a central set of useful documentation (as opposed to a sprawling assembly of docs in various states of disrepair). By putting all internal documentation in one place, we hope to make the information both easier to find and easier to maintain.

This project is maintained by the program management team, but contributions of any relevant documentation is highly encouraged. Please see [Contributing](https://jatic.pages.jatic.net/internal-docs/about/contributing/) for more details!

## Running locally

When editing, its very helpful to view the website locally to see live changes.

To view this website locally, do the following:

1. Clone the project
1. Install poetry through pip: `pip install poetry`
<<<<<<< HEAD
1. Install project dependencies through poetry: `poetry install --no-root` in the project root directory
   1. If you have a hangup on Keyring, add to your bashrc `export PYTHON_KEYRING_BACKEND=keyring.backends.null.Keyring` and re-source your bashrc.
1. In the project directory, run: `poetry run mkdocs serve`
1. Open the link in your browser at `http://127.0.0.1:8000/`
=======
2. Install project dependencies through poetry: 
   1. Navigate to the project directory then enter: `poetry install --no-root` "`--no-root`" prevents a somewhat meaningless error that occurs because there are no python files in the repo.
      1. You can increase verbosity by adding -vvv (number of v's indicated level of verbosity) `poetry -vvv install --no-root`.
      2. If you have a hangup on Keyring, add to your bashrc `export PYTHON_KEYRING_BACKEND=keyring.backends.null.Keyring` and re-source your bashrc.
   2. Wait until installation completes
3. Choose one of the following:
   1. Navigate to the project directory then enter: `poetry run mkdocs serve`
   2. Run mkdocs within the poetry environment
      1. Navigate to the project directory then enter: `poetry shell`
      2. `mkdocs serve`
4. Open the link in your browser (`http://127.0.0.1:8000/`)
>>>>>>> 60973fe ([README] Fixed typo in mkdocs build guide.)
