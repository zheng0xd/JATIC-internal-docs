# internal-docs

This is the central location for all internal documentation within the JATIC program!

Please view on pages: [https://jatic.pages.jatic.net/internal-docs/](https://jatic.pages.jatic.net/internal-docs/)

## Running locally

To view this website locally, do the following:

1. Install poetry through pip: `pip install poetry`
2. Install project dependencies through poetry: 
   1. Navigate to the project directory then enter: `poetry install --no-root` "`--no-root`" prevents a somewhat meaningless error that occurs because there are no python files in the repo.
      1. You can increase verbosity by adding -vvv (number of v's indicated level of verbosity) `poetry -vvv install --no-root`.
      1. If you have a hangup on Keyring, add to your bashrc `export PYTHON_KEYRING_BACKEND=keyring.backends.null.Keyring` and re-source your bashrc.
   1. Wait until installation completes
1. Install the [image processing dependencies](https://squidfunk.github.io/mkdocs-material/plugins/requirements/image-processing/). If you would not like to install these and still build locally, simply comments out the `- social` line under plugins within `mkdocs.yml`.
1. Choose of the following:
   1. Navigate to the project directory then enter: `poetry run mkdocs serve`
   1. Run mkdocs within the poetry environment
      1. Navigate to the project directory then enter: `poetry shell`
      1. `mkdocs serve`
1. Open the link in your browser (`http://127.0.0.1:8000/`)
