
# Software Requirements

The following specifies standards and requirements for a Python project's: structure, code design and standards, code style, documentation style, test suite, and maintenance regimen.

## Project Structure

The following is a description of the basic structure for a Python project that adheres to the [Python Packaging Authority](https://www.pypa.io/en/latest/)'s standards. This structure helps to ensure compatibility with 3rd party utilities and project analysis tools. [This tutorial](https://packaging.python.org/en/latest/tutorials/packaging-projects/) demonstrates the process for creating a project that adheres to this structure.

- Although not part of pypa's standard, we also suggest that modules and packages that are not part of a project's public API should have a leading underscore in its name, or it should reside in a directory whose name possesses the leading underscore.
- The project's Python source code should be isolated in a top-level directory named `src/`. This ensures that the Python package cannot be imported by the test suite unless the package has been installed locally.
- [Project metadata](https://packaging.python.org/en/latest/specifications/declaring-project-metadata/#declaring-project-metadata) should be specified in the `pyproject.toml` file or `setup.cfg` file when possible.
- A version string should be be accessible at runtime via the `__version__` attribute of the project's top-level Python module. See the section Versioning, Compatibility, and Maintenance Expectations for more details.
- Tools that have project-level configurations, such as `tox`, `coverage.py` and `isort`, should be configured using `pyproject.toml` when possible. Note that `flake8` and `pre-commit` do not support `pyproject.toml`. [`flake518`](https://github.com/carstencodes/flake518) is a small wrapper around `flake8` that provides support for `pyproject.toml`.
- The project's test suite should be in a `tests/` directory located at the top-level of the project.
- Public Python interfaces should include type annotations, and the project should include an empty `py.typed` file in its `src/`<lib_name> directory that is [included as part of the project's package-data](https://github.com/mit-ll-responsible-ai/responsible-ai-toolbox/blob/21142af92c3484e2aa670b3e09c1c70ba35c866d/pyproject.toml#L81-L82). This is to comply with [PEP 561's](https://peps.python.org/pep-0561/) specification for Python packages to distribute type information to users.
- A project that provides users with custom types – that are predominantly meant for use as type annotations – should provide them to users through a submodule named `.typing`.

The following is an example layout of such a project:

```
# structure of a Python project named 'jatic_vision'

jatic_vision/
├── LICENSE.txt
├── pyproject.toml
├── README.md
├── src/
│   └── jatic_vision/
│       ├── py.typed
│       ├── __init__.py
│       ├── models.py
│       └── _internals.py
└── tests/
    ├── conftest.py
    └── test_models.py
```

## Dependency Management

Projects should keep a clear account of their dependencies according to different categories. 

### **Note**: Two types of python imports

**Regular imports** are unguarded, meaning they will raise `ImportError` if the package cannot be imported:

```python
import third_party
```

**Guarded imports**, those which are able to do something else when importing the package fails. These will never give the end-user a bare `ImportError`, and there a few common patterns used to implement them:

Here is a simple example:

```python
try:
  import third_party
except ImportError:
  third_party = None

# later where third party may be used
def some_function():
  if third_party is None:
    raise Exception("package.some_function requires `third_party` be installed, install with pip install package[extra]")
```

You can also use an addition level of indirection with a test for the package.

```python
# package/_private_internal/needs_third_party.py
import third_party
def foo():
  ...

# package/__init__.py
if package_installed('third_party'):
  from _private_internal.needs_third_party import foo
  __all__.append('foo')
```

If the use of a third party package is limited in scope the import can be done inside a function.

```python
def foo():
  try:
    import third_party
    utility = third_party.some_function
  except ImportError:
    raise Exception("Something more descriptive")

  # or alternatively 
  except ImportError:
    utility = _fallback_some_function
  # where _fallback some function provides similar functionality, but third_party's version is preferred if it is installed. 
  ...
```

1. **Runtime Dependencies**: A package which is imported directly (e.g. not guarded by any checks) by the project's source code and is required for a critical piece of functionality. This is a package that must be available in the user's runtime environment, and without it importing part of the project's public API will lead to an `ImportError`. These packages will be using regular imports.
2. **Optional Runtime Dependencies**: Some projects may provide functionality which is not critical to the core use of that project. These features may require additional dependencies which can be made optional. An optional runtime dependency is one which a submodule providing such non-critical features would depend on. Considering an example, a package which provides some functionality for analysis may choose to provide some optional features for visualizing the results. Visualization features may require an additional plotting package dependency like `matplotlib`. It would be proper to classify `matplotlib` here as an optional dependency, and the features using it should be localized to a sub-module/package within the project and import of the part of the package is guarded by a check for the optional dependency such that an informative error is raised with a message like "Visualization features require matplotlib, install `mypackage-viz` to enable these extensions". These packages will be using one of the *guarded* import patterns described above. 
3. **Build/Development Dependencies**: These packages are not directly related to any functionality within the project itself, but developers should have them in the environment they use when working on the project. These may be used to enforce project code-quality regulations, and things like linters, formatters, and type-checkers. Would fall into the category. If a project has extensions which are compiled the appropriate toolchain, linked libraries and headers for building those extensions would also be included here.
4. **Testing Dependencies**: These are additional requirements beyond the runtime requirements of the project that are needed to execute the tests. The simplest example would be a testing framework like `pytest` which is commonly used to testing, but should almost never be a runtime dependency of the project. A less obvious example would be where a project is written in a way that is agnostic to the use of any particular framework, but the use of *some* framework would be required, say PyTorch vs. TensorFlow. The project may never directly import either of these tools, but in order to write tests mocking user input it would want to use one or both. In this case they are testing dependencies. 


### Dependency Versioning

Clarity and correctness are key when declaring the version requirements for a project's dependencies. In general they should be as un-restricted as possible, since any restrictions imposed by your project are in turn imposed on your users. A tool with very strict version requirements, especially on commonly used packages will have a hard time being adopted by users who may have their own requirements which will more easily conflict with strict rules.  The following guidance should be followed with respect to putting version requirements on runtime dependencies. 

- Lower Bounds: (e.g. `pkg >= 1.2.3`) Placing a lower version bound on a dependency is acceptable when it is found that any versions before the lower bound is incompatible, this may be due to an API break around a major version, for example. If the lower bound is a very recent release maintainer should consider implementing a work-around if practical to avoid this situation. 
- Exact Exclusions: (e.g. `pkg != 1.2.3`) These can be used when a known bug in the upstream dependency is found that affects the package in a critical way. These can also be made specific to a packaging ecosystem where upstream package has problems with metadata or is known to break environments in some way (such as the `pytorch != 2.0.0` issue affecting the pip ecosystem). If possible these exclusions should be linked to an upstream issue and tracked so that they can be removed in the future.
- Upper Bounds: (e.g. `pkg < 1.2.3`) Upper bounds are strongly discouraged on runtime and optional runtime dependencies, and should only be used temporarily. Upper bounds could be used to avoid a major version change of an upstream package which introduces API breaking changes. This would have a shelf life and be removed when the project is updated to be compatible with the new version of that dependency. A very relevant example would be for packages to exclude numpy 2.0+ during a period where they prepare for the change, then the upper-bound wold be moved to a lower bound when they are ready. 
- Exact Version Pins: (e.g. `pkg == 1.2.3`) Pins should generally be forbidden, only allowed after through investigation of alternative resolutions to the problem motivating them, and always linked to an issue. Should one be introduced it should be treated as a top priority to resolve the problem requiring the pin as quickly as possible, and having an exact version pin in the package metadata will be considered a blocker for releases. That is releases should never be published with hard pins. 
- Note: Some patterns suggested by Poetry are not explicitly mentioned here as they fall into one of the above categories. The `^`, `~`, and `*` versioning syntax are all sugar for defining upper/lower bounds so their use should follow the guidance above particularly with respect to setting upper bounds.

The use of upper-bounds, and exact pins in the build/development and testing dependency groups are less of an issue. This is because they 1) only affect the development team and those packaging the software, and 2) The environment used for development and packaging is often only used for that purpose and it is less likely that there will be a conflict with something else introduced to it.

The advice above related to the use of upper bounds is applicable for pure python packages. If your package has compiled
extensions (e.g. Cython, Pybind11) then there more details to guidance on how and when to use upper bounds. These
details are not discussed here. 


### Program Wide Dependency Requirements
The following packages are very popular and likely will be the dependencies for multiple program projects. In the spirit of ensuring compatibility between projects the following table outlines requirements for any program project depending on these libraries:

|Package     |Minimum Version   |Release Date   |Drop Date   |Py3.9| Py3.10 | Py3.11|Py3.12 | Latest Version | Latest Version Py 3.12|
|------------|------------------|---------------|------------|-----|--------|-------|-------|----------------|-----------------------|
|matplotlib  |3.7.1             |2023-4-3       |2025-3-3    |  y  | y      | y     | n     | 3.8.1          |     y                 |
|numpy       |1.24.2            |2023-5-2       |2025-5-2    |  y  | y      | y     | n     | 1.26.1         |     y                 |
|pandas      |2.0               |2023-2-4       |2025-1-4    |  y  | y      | y     | n     | 2.1.2          |     n                 |
|pytest      |7.3.1             |2023-14-4      |2025-13-4   |  y  | y      | y     | n     | 7.4.3          |     y                 |
|PyTorch     |2.1.1             |2023-4-10      |2025-3-10   |  y  | y      | y     | n     | 2.1.0          |     n                 |
|scikit-image|0.20.0            |2023-28-2      |2025-27-2   |  y  | y      | y     | n     | 0.22.0         |     y                 |
|scikit-learn|1.2.1             |2023-24-1      |2025-23-1   |  y  | y      | y     | n     | 1.3.2          |     y                 |
|scipy       |1.10              |2023-3-1       |2025-2-1    |  y  | y      | y     | n     | 1.11.0         |     y                 |
|torchmetrics|1.0.0             |2023-4-7       |2025-3-7    |  y  | y      | y     | n     | 1.2.0          |     n                 |
|tensorflow  |2.12.0            |2023-23-3      |2025-22-3   |  y  | y      | y     | n     | 2.13.1         |     n                 |
|python      |3.10              |2021-10-4      |2025-9-4    |     |        |       |       |                |                       |



## Packaging

Projects are required to publish packaged releases to PyPI and conda-forge. It is highly recommended that the build process is automated and tested frequently, such as by publishing nightly builds to private channels.

## Development Best Practices

It is a good idea to provide an environment specification for the use of developers, including runtime, testing and development dependencies which can be used to quickly set up a development virtual environment. When building this environment specification the following suggestions should be considered:

- Dependencies which have a lower bound should be pinned to the oldest supported version. This will ensure that developers don't produce code which uses features outside the supported set. 
- Those dependencies used for CI checks and testing, such as linters, and type checkers, should be set to the versions used in the CI jobs to minimize discrepancies between results produced locally and those produced by the automated workflow. 
- The artifacts/instructions for generating this developer environment should not assume or limit the developer to a particular packaging/virtual environment system (it should support both pip and conda). 
- Provide aggregation tooling for style enforcement checks like linters and formatters. A developer should be able to run the formatting pass and linter check (over their modifications only) with a single command. `pre-commit` can be used to set this up as a pre-commit hook. 

## Project Test Suite

A JATIC Python project is to maintain an automated test suite. The primary distinction between a collection of manual tests versus an automated test suite is that, for the latter, a single command line call can collect, run, and report the results of all (or a subset of) a suite's tests. The project's automated test suite should leverage the following:

- The [pytest framework](https://docs.pytest.org/) for collecting, initializing, and running tests.
  - The standard library's `unittest` module can be relied on for mocks, monkey patches, and doctests, all of which can be leveraged within a pytest-driven test suite. Otherwise, `unittest` should not be used as a test-runner and pytest-style test functions should be preferred over `unittest`-style test classes.
  - The `nosetest` framework is no longer maintained and should not be used.
- [`tox`](https://tox.readthedocs.io/en/latest/) for automating the process of building isolated test environments, installing dependencies, and the subject via pip packaging, and running tools (e.g. running tests in a Python 3.10 environment against the nightly build of PyTorch). `tox` helps normalize the process of running automated jobs across platforms (e.g. the same tox job-launch commands can be used on local machines as well as on CI/CD servers).
  - `tox` should be used to run a project's test suite across all supported Python versions.
- CI build and test matrices automate the same processes as `tox`, but can be used with multiple packaging systems.
  - These features are similar to configure, and supported by both Gitlab pipelines, and Github actions.
- The [`coverage.py`](https://coverage.readthedocs.io/en/coverage-5.3/) tool (with the [pytest-cov plugin](https://pypi.org/project/pytest-cov/)) to track the parts of the project's codebase that are and are not exercised by the test suite. Projects are free to specify their own code-coverage requirements (e.g. 85% code coverage), or to forego having a specific coverage requirement. That being said, the project's coverage metrics should be reported by a tox job.
- [pyright](https://github.com/microsoft/pyright) is a fast type checker that performs incremental updates when files are modified.

Teams are advised to read through this [introductory tutorial to property based testing](https://github.com/rsokl/testing-tutorial). [Property-based testing](https://increment.com/testing/in-praise-of-property-based-testing/) is an effective approach to testing scientific software for which functions often cannot be tested against "oracles" (i.e. sources of known correct outputs for diverse inputs to functions).

Explicit DevSecOps pipeline requirements that will be enforced via GitLab CI/CD can be found in the [DevSecOps Testing Requirements](./DevSecOps%20Testing%20Requirements.md) document.

### Testing Environment
Projects should test a variety of Python, and dependency versions. However testing under all possible combinations of compatible dependencies is impractical the following guidelines should be followed when building a matrix of test environments:

- The unconstrained package metadata should be used in at least one test environment for each packaging system supported. That is to say, you should have a default solve with both pip and conda in CI. This is meant to reflect what the end-user would experience if they were to install the project from scratch.
- Test Environments should cover optional dependency configurations.
- In general, it's wise to test the oldest supported versions of your critical dependencies, as well as the most recent. The former ensures that your lower bounds are still correct; the latter mimics fresh installations.

## Versioning, Compatibility, and Maintenance Expectations

A Python package's releases should utilize [semantic versioning](https://semver.org/) (i.e. the version number is structured as `MAJOR.MINOR.PATCH`).

- Projects like [setuptools scm](https://github.com/pypa/setuptools_scm/) and [versioneer](https://github.com/python-versioneer/python-versioneer) can be used to extract a project's version string from version control metadata (e.g. a tag name from git). Using such a tool is recommended as it helps to eliminate from a project's release process the manual, error-prone steps of updating an embedded version string.

## Code Design, Standards, and Guidelines

[Python code should comply with the JATIC Python Coding Guidelines](./guidelines/Python%20Coding%20Guidelines.md). These should be followed for new code. Existing code can be permitted to ignore guidelines until time is allocated to revise and update the code.

### Code Style and Formatting

Adhering to a clear and consistent style is critical for writing maintainable code, especially when coordinating multi-organization collaborations. That being said, enforcing such standards can be tedious and labor-intensive. Fortunately, several powerful tools exist that can help automate consistent code styling. Compliance with the [Python Coding Guidelines](./guidelines/Python%20Coding%20Guidelines.md) should help create consistent style. Additional style and formatting consistency should come by application of formatting tools.

JATIC Python projects should leverage the following automated tools for formatting code and for enforcing style:

- [black](https://black.readthedocs.io/en/stable/): is a PEP 8 compliant opinionated code formatter. It is designed to be run on a project's source code and tests in order to modify these text files in-place so that the resulting files have canonicalized formatting. black is limited in the ways that it can be configured; this is by-design so that teams do not spend time squabbling over things like white-space conventions. Note that [black can be run on Jupyter notebooks](https://black.readthedocs.io/en/stable/getting_started.html#installation) as well.
- [isort](https://pycqa.github.io/isort/): sorts imports in alphabetical order and into sections (e.g. std-lib imports, third-party imports, and first-party imports). Vendors should [configure isort to be compatible with black](https://pycqa.github.io/isort/docs/configuration/black_compatibility.html) according to these instructions.
- [flake8](https://github.com/PyCQA/flake8): analyzes your code to enforce the PEP8 standards and to catch bad code patterns, such as unused imports and variables. This is not an auto-formatter, rather when it is run from the command line it will generate a report of code style violations in a code base, which includes their locations and error codes. Vendors can [configure flake8](https://flake8.pycqa.org/en/latest/user/configuration.html) to skip particular files (e.g. one may want to avoid scanning a `.py` file that was auto-generated by the Sphinx documentation framework).

At its most basic level, our code style standards for Python-based projects are derived from the [PEP 8 Style Guide](https://peps.python.org/pep-0008/), with additional formatting specifications that are best summarized as "let auto-formatters do their thing". It is recommended that these three tools be applied in an automated fashion. [Pre-commit hooks](https://pre-commit.com/) make it simple to run these tools on a per-commit basis, and CI/CD processes should be designed to apply/enforce these tools before a branch can be merged into protected branches (e.g., `dev`, `main`). [Here is an example of a pre-commit configuration file](https://github.com/mit-ll-responsible-ai/responsible-ai-toolbox/blob/main/.pre-commit-config.yaml) (and an accompanying [isort config](https://github.com/mit-ll-responsible-ai/responsible-ai-toolbox/blob/21142af92c3484e2aa670b3e09c1c70ba35c866d/pyproject.toml#L86-L89)) that runs these three tools.

## Documentation

JATIC projects should utilize consistent conventions and styles in their documentation strings, documentation websites, and in the organization of tutorials, how-to guides, and other instructional materials. Guidance on documentation within code can be found in [Python Coding Guidelines](./guidelines/Python%20Coding%20Guidelines.md)

### Project Documentation
Project documentation should leverage [the Sphinx project](https://www.sphinx-doc.org/en/master/) to generate hierarchical documentation in HTML (or LaTeX for a printable version). Using the [reStructuredText](https://docutils.sourceforge.io/rst.html) markup language for the source content recommended over markdown. The [PyData Sphinx Theme](https://pydata-sphinx-theme.readthedocs.io/en/stable/) is recommended for providing, e.g., the css styling, fonts for the HTML pages; it is popular, actively supported, and includes rich features like code-tabs and a dark-theme.

Documentation should follow the guidance in [Python Coding Guidelines](./guidelines/Python%20Coding%20Guidelines.md).

### Documentation Organization

It is recommended that projects leverage the [Diátaxis framework](https://diataxis.fr/) for technical documentation authoring. This prescribes four "modes" of documentation – tutorials, how-to guides, explanations, and technical reference – for introducing users to a project. This can help to create a consistent learning experience for users who are leveraging multiple JATIC projects, and it helps to save JATIC vendors from "reinventing the wheel" when it comes to writing project documentation. A "change log" should also be maintained, detailing the release notes of the project's respective versions, as part of the documentation site.
