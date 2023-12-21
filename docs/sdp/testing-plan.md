# Testing Plan

## Expectations

As described in the Software Requirements section of the SDP, a vendor is expected to develop and maintain an automated test suite using the `pytest` framework. The test suite should be able to be run in a Python environment that has installed the vendor's package via the command `pytest tests/`. Additionally, a `tox` configuration is to be maintained by the vendor, that supports the following:

- Running the tests that involve all of the required installation dependencies against each supported version of Python.
- Running the test suite in an environment that excludes all optional dependencies (i.e., confirming that optional dependencies are indeed optional).
- Measuring the test suite's code coverage.
- Running the tests that involve all of the package's optional installation dependencies.
- Running tests against the minimum dependency versions that the package is documented to support.
- Running tests against either the dependency versions that the package is documented to support, or, if no such version upper-bound is specified, against the nightly/master builds of the dependencies.

The organizers of the SDP will run vendor-submitted code through tests that include:

- Verification that the project's structure adheres to the software requirements. This includes checks on the project's metadata and documentation as well.
- Verification that the project's code adheres to the style guidelines, as implemented by the automated tools that were specified by the software requirements.
- Exercising the project's test suite via its `tox` jobs.
- Running a spell checker on the project's documentation.
- Running security scans.

## Capabilities

The project's test capabilities should abide by the following.

### Unit tests

A unit is the smallest piece of code to be tested in a test suite, and it is typically considered to be a single non-trivial function. Unit tests always use white-box testing techniques, where the inner workings of the unit being tested are known to the tester.

### Integration tests

Integration tests utilize a combination of white-box and black-box techniques to test a group of individual units as a single component. It is often simply testing the implementation of a single public interface. A project's test suite should prioritize integration tests of its public APIs over unit tests of internal functions.

### Regression tests

The purpose of regression testing is to ensure that modifications in software have not caused unintended adverse side effects. Regression testing should be conducted after any change to the codebase to prevent the introduction of new bugs. 

### System tests

A project's test suite should include a small number of system tests whereby the entire application is tested through an end-to-end process. This type of testing is very slow, so it should be kept to a bare minimum. System testing is limited to black-box techniques, where the tester has no knowledge of the underlying code. These tests may test the usability, scalability, compatibility, or performance of the application.

### Property-based tests

Testing scientific software, such as neural networks, can be challenging as there is often no "oracle" – a source that will tell us what the expected output of a function will be – against which to test. For example, given an input to a neural network, it may not be possible to predict *precisely* what the network's outputs should be. In these cases it is useful to identify general properties of the function, e.g., a neural network is typically equivariant under batch-ordering, that can be tested under highly diverse inputs. Vendors are encouraged to utilize property-based testing in their test suites both in the context of unit tests and integration tests.

### Static type checking

[pyright](https://github.com/microsoft/pyright) is the static type checker that VSCode's Python extension is built off of. The `jatic_toolbox`  provides a Python API for running pyright on both Python code and documentation that contains Python code examples. A vendor should leverage these capabilities to include in their test suite:

- Validate the type annotations of the project's public APIs, demonstrating that type checkers correctly flag "true positives" wherein users specify inputs of incorrect types, and that pyright returns a "clean scan" for correct usages of the interfaces.
  - It is recommended that vendors include a pyright scan of the entirety of their internal code base, but this is not required.
- Runs pyright on the following parts of a project to verify that they do not contain unexpected errors:
  - The `Examples` sections of the docstrings for all publicly-facing Python interfaces.
  - All documentation files (i.e., restructured text files), to validate their Python code blocks.
  - Jupyter notebooks that are included in the project (e.g., as demos).

### Test results reporting

A project's tox configuration should include jobs that can be run to report the following:

- The code coverage of the pytest test suite, via [coverage.py](https://coverage.readthedocs.io/en/6.3.3/index.html). Refer to the Software Requirements for more details.
  - Code coverage reported by pytest's code coverage report must be ≥ **90%** [explicitly mark code blocks that they do not intend to cover](https://coverage.readthedocs.io/en/7.0.4/excluding.html) with their tests, and eventually enforce 100% code coverage once the project is sufficiently mature.
- A pyright [type-completeness score](https://github.com/microsoft/pyright/blob/92b4028cd5fd483efcf3f1cdb8597b2d4edd8866/docs/typed-libraries.md#verifying-type-completeness), using the  `--ignoreexternal` flag. This should report 100% type completeness for the project's public API.
- A [bandit](https://bandit.readthedocs.io/en/latest/) security scan report.

