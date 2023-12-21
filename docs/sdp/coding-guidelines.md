# Python Coding Guidelines

## Purpose

This document specifies the coding guidelines for coding in Python for the project.
Guidelines help improve consistency across the tools created as part of the JATIC program.

They should be:
- Flexible: exceptions to adherence to the guidelines are permitted, particularly if the guideline prevents implementation of a desired feature.
- Evolving: Feel free to suggest additions or changes to the guidelines.


## Python Version

We use the currently supported major version of Python per the [python version graph](https://devguide.python.org/versions/).  The exact version of Python or library dependencies is not authoritatively captured in non-executable documents but captured in executable configuration or scripts.  In other words, we will declare the versions of Python that this project is targetting but rely on configuration files running in CI to enforce the list.

According to the Python version graph, each version of Python has three distinct phases:

    1. Active: During this phase, the version of Python receives regular bugfixes, security patches, and feature enhancements.
    1. Maintenance: Once a version reaches maintenance mode, it no longer receives new features or bugfixes but only critical security patches.
    1. End-of-Life: When a version reaches End-of-Life (EOL), it is no longer supported.

A good place to look for the current versions of Python that the project is considered Active is in the `pyproject.toml` file in a repository's root folder.  There is a `python` version listed in that file that might be considered the main version but this project considers many Python versions for compatibility.  The list of current Python versions that are considered is captured in the matrix configuration of `tox`.  Tox has a list of Python versions that our tests and builds iterate through, checking each one.

In plain text, the list of Python version is:
    - 3.8
    - 3.9
    - 3.10
    - 3.11
where the patch level version of each of those Python versions is up to date with high and critical vulnerability notices from CVE websites such as [MITRE's](https://cve.mitre.org/) or [NIST's](https://nvd.nist.gov/vuln).

To determine the supported versions of Python that we should use, we generally follow the timeline and guidelines provided by the Python development community. The Python version graph (<https://devguide.python.org/versions/>) shows a sliding support window for different Python versions.  Scientific Python has [a sliding support window graph](https://scientific-python.org/specs/spec-0000/) that features many libraries.

Our goal is to remain within the Active or Maintenance phases for all the Python versions and dependencies.  Although a strict time period or version range has not yet been selected, it should be an ongoing and reasonable security practice that is recognizable in the context of the projects and software we are using.  The exact versions will change over time and those details should not be captured in Markdown but in things that are executing in the CI/CD pipeline.

ℹ️ There is more detail in [Software Requirements](../Software%20Requirements.md)


## Supported/Required Dependencies and Tool Versions

The general dependency strategy is the same as the Python Version section.  Dependencies have support lifecycles, sometimes no support but an open-source community and signals that a version should not be used.  Dependencies have dependencies and there is little value in documenting this graph as human readable markdown.

The specific versions of dependencies (e.g., Python version) supported/required by your repo should be specified at the top of the repo's top-level README.md. For example, [like this](https://gitlab.jatic.net/jatic/cdao/jatic-toolbox/-/blob/main/README.md).

Per [requirements to use poetry to manage Python dependencies](../Software%20Requirements.md), the dependency versions should be verified by poetry by inclusion in the repo's [`pyproject.toml` file](https://gitlab.jatic.net/jatic/cdao/jatic-toolbox/-/blob/main/pyproject.toml#L15). They should also be contained in a [`.tools-version` to be verified by asdf](https://asdf-vm.com/manage/configuration.html#tool-versions) in the CI/CD pipeline.


## PEP8

We adhere to PEP8 with two exceptions:

- PEP8 suggests using a line length limit of 79, but JATIC projects have a range within which they should stay: 79-150.
Based on [PEP guidance on this subject](https://peps.python.org/pep-0008/#maximum-line-length) it makes sense to limit width. Also, line length should be limited consistently within a repo. Line length must be no longer than 140. We suggest something smaller like 99 or 120 as a good compromise between narrowness for side-by-side and the readability of fewer continuations.

- We define the `__all__` variable in each Python module. The contents of `__all__` should only be content that you want exported from the package. The `__init__.py` file should then include import wildcards. To be clear, leading underscores should be used for private variables and functions that should not be used outside the file. Objects without leading underscore and not within `__all__` are intended to be usable within other files in the package, but not exported outside the package.
- Your Python modules should never use a wildcard import to import all from a module.
- Aside from that, a leading underscore is sufficient to indicate private variables, functions or methods:

```
# Bad:
# Contents of `my_package/second_module.py`
from my_package.my_module import *  # Do not import "*"

# Good:
# Contents of `my_package/my_module.py`
__all__ = [public_function]
def public_function():
    pass

def private_function_for_package():
    pass

def _private_function_within_module():
    pass

# Contents of `my_package/second_module.py`
from my_package.my_module import private_function_for_package, public_function

# Contents of `__init__.py`
from my_package.my_module import *
```

## In Addition to PEP8
PEP8 leaves many things open. These are additional guides or choices/opinions to choose from options suggested by PEP8.
python
## Types
A JATIC Python project's interfaces should leverage consistent type annotations across interfaces, which serve as concise, legible, and verifiable documentation. Publicly-facing interfaces should prioritize the use of standard-library types (e.g. `int`  or `dict`), common third party data types (e.g. `torch.Tensor`), or structural subtypes (a.k.a. protocols as specified in [PEP 544](https://peps.python.org/pep-0544/)) over the introduction of custom types. An additional document that motivates use of typed interfaces for JATIC projects will be provided. Resources for best practices for writing and maintaining type annotations can be [found here](https://typing.readthedocs.io/en/latest/#guides) and [here](https://github.com/microsoft/pyright/blob/92b4028cd5fd483efcf3f1cdb8597b2d4edd8866/docs/typed-libraries.md#best-practices-for-inlined-types).

### Documentation and Docstrings
We use docstrings of widely-adopted styles that allow direct generation of documentation via Sphinx. Allowed styles are, for example, [NumPy Documentation Style](https://numpydoc.readthedocs.io/en/latest/format.html#docstring-standard) or [Google-style docstrings](https://google.github.io/styleguide/pyguide.html#383-functions-and-methods). [Examples in docstrings must follow the Doctest format](https://docs.python.org/3/library/doctest.html). These docstrings must be used to autogenerate documentation with Sphinx.
Internal functions do not require docstrings. Functions part of the public API require docstrings.

Items in the `Parameters` section should include types. For a tensor-like parameter with constraints on its shape, its shape pattern should be included alongside its type information. E.g. a batch of images may appear in the `Parameters` section as: `batch: torch.Tensor, shape-(N, C, H, W)` where `N` is the batch size and `(C, H, W)` is the shape of a single image. Interfaces (functions, classes, etc.) that are part of a code base's public API should include an `Examples` section. Here is a [link to example docstring](https://github.com/mit-ll-responsible-ai/responsible-ai-toolbox/blob/caebefe51e220818d524283959a42fd29852a3ce/src/rai_toolbox/perturbations/solvers.py#L43-L206).

The [numpydoc Sphinx extension](https://numpydoc.readthedocs.io/en/latest/) can be used to generate reference documentation for the project for Numpy-style docstrings. [Napoleon Sphinx extension](https://www.sphinx-doc.org/en/master/usage/extensions/napoleon.html) can work for Google-style or Numpy-style. This enables Sphinx to parse and render NumPy-style documentation strings.

Much code should be self-documented by its writing and naming, making docstrings unnecessary. For non-public-API functions, docstrings are up to the discretion of the writer.

### Quotes
Use double quotes " , not single quotes '. This choice adheres to things like [PEP257](https://peps.python.org/pep-0257/).

### Naming Conventions

[PEP8 has much content on naming conventions.](https://peps.python.org/pep-0008/#naming-conventions)
Follow those conventions. Some notable ones for ease of reference:
- Functions: `snake_case`
    - Names that are visible to the user as public parts of the API should follow conventions that reflect usage rather than implementation.
    - See content above on `__all__` definition on handling objects that should be public or available within the package, but not public (neither should have leading underscore; public objects should be in `__all__` and available within the package should not).
    - _single_leading_underscore: For internal variables or functions that should be used only within the file.
- Classes: `CapWords`
- Types: `CapWords`
- Constants: `ALL_CAPS`
- Function: `snake_case`
- Packages/module names: `snake_case`
- Variables: `snake_case`
    - df_ prefix for Pandas data frames
    - _file_path suffix for file path strings
    - Unit suffixes for variables with non-standard units, and only for those. In particular, radians are the standard unit for angles.
    - The use of explicit, descriptive data structures – e.g., named tuples, dataclasses, and xarrays – should be used to store heterogeneous data. For example, accessing latitude & longitude coordinates by name – `coord.lat`  and `coord.lon`  – is preferred to accessing them by index as `coord[0]`  and `coord[1]`.
- Modules:
  Care must be taken to distinguish those parts of a JATIC project that comprise its public Python API from those that do not. This is chiefly accomplished by leveraging a leading underscore in the names of private modules and packages. It can be helpful for developers to use an `_internals` subpackage that contains the majority of the package's implementations, and to populate public namespaces purely via imports from parts of `_internals`.
```
# Bad
distance_meters = 4.0
angle_limit = 89.0

# Good
distance = 4.0
angle_limit_degrees = 89.0
```

### Passing Arguments by Keyword

Our default behavior is to pass function arguments by keyword rather than by position, for safety, maintainability, and readability. More specifically, the following guideline applies:

- Function takes one argument: It’s up to you whether to pass by keyword or by position.
- Function takes two or more arguments: Pass by keyword.
- Exceptions: No need to pass by keyword if both of the following conditions are true:
    - The respective arguments and their positions are common knowledge (e.g. the start, stop, and step arguments, but you should pass by keyword for any of its additional arguments).
    - The signature of the function is very unlikely to ever change (e.g. Python built-ins like range, standard library packages, mature libraries like NumPy, but not immature libraries like TensorFlow 0.8)
- Note that both of the requirements for the exception case above will rarely be met by functions from your own code base, i.e. you can most often not assume that the arguments to your function are common knowledge and that its signature is not going to change.

#### Example:
```
def foo(yaw, pitch, roll, sausages, mode):
    pass
# Bad:
foo(1.57, -0.36, -1.57, 2.0, 'eggs')  # Let's pray that the order of yaw, pitch, roll will never change!

# Good:
foo(yaw=1.57, pitch=-0.36, roll=-1.57, sausages=2.0, mode='eggs')
```

### Instance Attribute Definition
Instance attributes should all be defined in __init__() so that it is easy to see what instance attributes a class has:

```
# Bad:
class foo:
    def __init__(bar):
        self._bar = bar

    def func():
        self._baz = 42  # Instance attribute defined outside __init__

# Good:
class foo:
    def __init__(bar):
        self._bar = bar
        self._baz = None

    def func():
        self._baz = 42
```
### Output Strings
When you need to insert values of variables into strings, don’t add strings together. In Python 3, use [f-strings](https://realpython.com/python-f-strings).

### Example:
```
foo = 4
bar = math.pi

# Bad:
string = str(foo) + " apples and " + str(bar) + " radians"
string2 = "".join([str(foo)," apples and ", str(bar), " radians"])

# Good (Python 3):
string = f"{foo} apples and {bar:.2f} radians"
print(f"I like to eat {foo} apples")
```

### Keyword Strings (Enums)
Keyword strings should be defined as enums whenever it makes sense (and it very often makes sense). It always makes sense if the respective keyword is used more than once. Doing this prevents errors, makes the code a lot more maintainable and traceable, makes possible editor features like “go to definition”, code completion, smart refactoring, etc.

```
# Bad:
# In foo.py
MyFunction.add(name="SET_INIT_MODE",  # Ok if only used once in code
               SetMode(key_name="mode",  # Bad because used repeatedly
                       value="init"))  # Bad because used repeatedly

# Good:
# In foo.py
from enum import Enum

action_params = Enum('ActionParams',
                     names={MODE: 'mode',
                            STATE: 'state'},
                     type=str)

mode_params = Enum('ModeParams',
                            names={INIT: 'init',
                                   ERROR: 'error'},
                            type=str)

MyFunction.add(name="SET_INIT_MODE", # Ok if only used once in code
                 SetMode(key_name=action_params.MODE,
                         value=mode_params.INIT))
```

### Command Line Interface (CLI)
Argparse [(tutorial)](https://docs.python.org/3.8/howto/argparse.html) is the standard for defining command line interfaces (CLI). Other packages for handling CLI can be used that make handling CLI easier, such as [hydra-zen](https://pypi.org/project/hydra-zen/).

### Type Hints
Always use [type hints](https://realpython.com/lessons/type-hinting) both for parameters and returns. They make the code a lot easier to understand and, more importantly, enable type checking. [PEP484](https://peps.python.org/pep-0484/) is well worth a skim to get a deeper understanding of type hints.

Type checking must be added in the CICD pipeline for your repo. PyRight is an example of type checker you can use.

[For more examples and details, see here.](https://mypy.readthedocs.io/en/stable/cheat_sheet.html)

#### Example:

```
# Bad:
def foo_bar(data, groupby, bounds, baz, crazy_param = 42):  # Nobody knows what type these are
    pass

# Good:
import pandas as pd
from typing import Any, Mapping, Sequence, Tuple, TypeVar, Union

BoundsDict = Mapping[str, Tuple[float, float]]  # We can define type aliases
T = TypeVar('T', pd.DataFrame, str, float, None)  # We can define arbitrary types

def foo_bar(
        data: pd.DataFrame,
        groupby: str,
        bounds: BoundsDict,
        baz: Union[int, Sequence[int]],
        crazy_param: Any = 42,
) -> None:
    pass
```
Some notes:

- The [typing module](https://docs.python.org/3/library/typing.html#module-typing) provides support for type hints.
- The [typing extensions module](https://github.com/python/typing_extensions) provides support for older Python protocols and version.
- Type hints support dynamic programming with types such as [Union](https://docs.python.org/3/library/typing.html#typing.Union) and [Any](https://docs.python.org/3/library/typing.html#typing.Any).
- Type checking is consistent with Python’s [numeric hierarchy](https://peps.python.org/pep-3141). A particularly important example of this is that int is a sub-type of float, therefore, if you want e.g. a parameter to accept both int and float, it’s sufficient to annotate the parameter with the parent type float instead of Union[int, float].
- [There is a difference between TypeVar and Union.](https://stackoverflow.com/questions/58903906/whats-the-difference-between-a-constrained-typevar-and-a-union)

### Vectorization / NumPy
Prefer vectorized operations (i.e. [NumPy](https://realpython.com/numpy-array-programming)) over loops wherever possible. Loops in Python are very slow and therefore to be avoided for stuff like arithmetic operations if possible. Note that the `numpy.vectorize()` function itself is slow and really just a loop. See [Notes section here](https://numpy.org/doc/stable/reference/generated/numpy.vectorize.html).:

```
# Bad:
sum = 0
for i in long_list:
    sum += i

# Good:
import numpy as np

array = np.array(long_list)
sum = np.sum(array)  # Implemented in C and much, much faster
```

### Parentheses in Class Definitions
Do not add obsolete empty parentheses to class definitions if you don’t inherit from anything:

```
# Bad:
class MyClass():

# Good:
class MyClass:
```

### Default Argument Values
A function signature's default values should not reflect narrow, application-specific choices. For example, it would be inappropriate for a function for training a neural network to specify the following arbitrary, unjustified default values

`def train(batch_size: int = 10, num_train_steps: int = 100): ...`

Such defaults can bias users to overlook important settings that they should determine for their application. Instead, `batch_size` and `num_train_steps` should not specify any default values.

### Mutable Default Arguments
Do not use mutable default arguments. In particular, lists and dictionaries in Python are mutable, so do not use those as default arguments. Reason: Default arguments in Python are initialized only once during the execution of the function definition code and then never again. Therefore, if a mutable default argument gets modified inside the function body, it will be modified for all future calls of that function. [This short article](https://docs.python-guide.org/writing/gotchas/#mutable-default-arguments) explains the problem nicely. Two examples, the second of which is from the linked article:

```
# Bad:
def foo(cookie_orders=[3, 3, 3]):
    # Let's hope nobody modifies `cookie_orders` inside the function
    pass

# Good:
def foo(cookie_orders=(3, 3, 3)):
    # No risk here, tuples are immutable
    pass

# Bad:
def append_to(element, to=[]):
    to.append(element)
    return to

# Good:
def append_to(element, to=None):
    if to is None:
        to = []
    to.append(element)
    return to
```

### Initialization of Common Data Structures
When creating a new common data structure such as a list, dictionary, or tuple, use the explicitly named constructor function instead of pairs of brackets. Preference is strong when the structure is created empty. When initializing a filled list, dict, or tuple, it is better and easier to do with brackets/parentheses/braces.

```
# Least Ok:
new_list = []
new_dictionary = {}
new_tuple = ()

# Ok
new_filled_dictionary = dict(a_key=1, another_key=2)
# Lists and tuples can also be initialized with their function names.

# Good:
new_list = list()
new_filled_list = [[1, 2, 3], [4, 5, 6]]
new_dictionary = dict()
new_filled_dictionary = {"a_key": 1, "another_key": 2}
new_tuple = tuple()
new_filled_tuple = ([1, 2, 3], [4, 5, 6], [7, 8, 9])
```

### Class Decorators
[Class decorators](https://peps.python.org/pep-0318/) should be used to identify static and class functions, but they can be used for other purposes as well.
[Guidance on how to use class decorators can be found online.](https://realpython.com/primer-on-python-decorators/)
