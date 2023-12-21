# DevSecOps Testing Requirements

- [DevSecOps Testing Requirements](#devsecops-testing-requirements)
  - [Expectations](#expectations)
  - [Capabilities](#capabilities)
    - [Code Coverage](#code-coverage)
    - [Unit tests](#unit-tests)
    - [Integration tests](#integration-tests)
    - [Regression tests](#regression-tests)
    - [Static Application Security Testing (SAST)](#static-application-security-testing-sast)
    - [Dependency Scanning](#dependency-scanning)

## Expectations

The following requirements will be enforced on all vendor projects running within JATIC GitLab CI/CD. Failure to pass the following test critera will result in failed CI builds, and the inability to progress forward in the JATIC DevSecOps pipeline.

## Capabilities

The project's test capabilities should abide by guidance in the Testing Plan section of the SDP and will be enforced via CI/CD.

### Code Coverage

:star: **Requirements:** :star:

- Code coverage reported by pytest's code coverage report must be ≥ **90%**.

### Unit tests

Unit tests should be small and fast, therefore they should not interact with components that are slow or external to the application, such as databases. Calls to slow or external components should be mocked, stubbed, or avoided when writing unit tests.

It is important to identify and test the unit's critical execution path, however it is usually impossible to test every corner case. It is recommended that a vendor use its coverage report to verify that the unit's critical execution paths have been thoroughly tested, and to identify areas of code that are not being tested.

:star: **Requirements:** :star:

- Unit tests must be run in the CI/CD pipeline.
- pytest must be used to run tests of every function. 

**Recommendations:**

- Tests should cover inputs that span edges, beyond expected ranges, at limits, near limits, wrong types, too many inputs, across the span of potential issues, etc.
- Since unit tests are relatively inexpensive, we recommend writing many tests of inputs to ensure coverage of potential behavior of the code.
- Unit tests should be completed prior to and separately from integration tests.

**Code Example:**

```
# content of conftest.py

# we define a fixture function below and it will be "used" by
# referencing its name from tests

import pytest


@pytest.fixture(scope="class")
def db_class(request):
    class DummyDB:
        pass

    # set a class attribute on the invoking test context
    request.cls.db = DummyDB()
```

```
# content of test_unittest_db.py

import unittest
import pytest


@pytest.mark.usefixtures("db_class")
class MyTest(unittest.TestCase):
    def test_method1(self):
        assert hasattr(self, "db")
        assert 0, self.db  # fail for demo purposes

    def test_method2(self):
        assert 0, self.db  # fail for demo purposes
```
[Example reference](https://docs.pytest.org/en/7.1.x/how-to/unittest.html)

_[Back to the top](#devsecops-testing-requirements)_

### Integration tests

Integration tests should typically focus on behavior over implementation: verifying the correctness of a function's outputs under diverse inputs is more important than using techniques like mocks to check how a function arrives at its results.

Unlike unit tests, integration tests don't need to be small and fast. They may involve testing a component's integration with a database or external service. For such tests, a vendor should ensure that the database or external service is started and stopped automatically, either as part of the test code or in the tox configuration.

:star: **Requirements:** :star:

- Integration tests must be written incrementally using a [Top Down](https://www.tutorialspoint.com/software_testing_dictionary/top_down_integration_testing.htm) strategy.
- Integration tests must be run in the CI/CD pipeline.

**Recommendations:**

- Business logic requirements/inconsistencies should be tested for prior to integration tests.
- Enable verbose test logging configurations to allow for maximum insight into integration testing failures between modules.
- Define a custom pytest marker to decorate integration tests.
- Integration tests should be completed prior to and separately from system tests.

**Code Example:**

```
# contents of pytest.ini

[pytest]
markers =
    integration: marks tests as integration (deselect with '-m "not integration"')
    serial
```

pytest markers can also be registered in a [pytest_configure](https://docs.pytest.org/en/latest/reference/reference.html#pytest.hookspec.pytest_configure) hook:

```
def pytest_configure(config):
    config.addinivalue_line(
        "markers", "integration: mark tests as integration"
    )
```
[Example reference](https://docs.pytest.org/en/latest/how-to/mark.html#registering-marks)

_[Back to the top](#devsecops-testing-requirements)_

### Regression tests

 Considering the negative domino effect that can occur to a system whenever introducing new code (specifically when modifying core features), regression testing allows developers to pinpoint exactly where new bugs may have been introduced, helping to close the feedback loop inherent with agile software development. Test cases for new code should be written before the code can be considered complete.

:star: **Requirements:** :star:

- All new code introduced into the codebase must be tested.
- All bugs introduced by new code should be reported and tracked within GitLab.

**Recommendations:**

- Vendor teams should define a regression testing strategy that includes the most important test cases and frequency of testing.
- Previously executed test results and test plants should be available to be used as a "known working state" becnhmark for regression tests.
- Utilize pytest plugins such as [regtest](https://pypi.org/project/pytest-regtest/) to compare output against previously executed tests, after new code has been introduced.

**Code Example:**

The pytest-regtest plugin provides a fixture named regtest which can be used as a file handle for recording data:

```
    def test_squares_up_to_ten(regtest):

        result = [i*i for i in range(10)]

        # one way to record output:
        print(result, file=regtest)

        # alternative method to record output:
        regtest.write("done")

        # or using a context manager:
        with regtest:
            print("this will be recorded")
```

If you run this test script with pytest the first time there is no recorded output for this test function so far and thus the test will fail with a message including a diff:

```
$ py.test
...

regression test output differences for test_demo.py::test_squares_up_to_ten:

>   --- current
>   +++ tobe
>   @@ -1,2 +1 @@
>   -[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
>   -done
>   +
```

The output tells us what the current output is, and that the "tobe" output is still empty.

For accepting this output, we run pytest with the --reset-regtest flag:

```
$ py.test --regtest-reset
```

Now the next execution of py.test will succeed and we can break the test by modifying the code under test to compute the first eleven square numbers:

```
    from __future__ import print_function

    def test_squares_up_to_ten(regtest):

        result = [i*i for i in range(11)]  # changed !

        # one way to record output:
        print(result, file=regtest)

        # alternative method to record output:
        regtest.write("done")
```

The next run of pytest delivers a nice diff of the current and expected output from this test function:

```
$ py.test

...
>   --- current
>   +++ tobe
>   @@ -1,2 +1,2 @@
>   -[0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
>   +[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
>    done
```

[Example reference](https://pypi.org/project/pytest-regtest/)

_[Back to the top](#devsecops-testing-requirements)_

### Static Application Security Testing (SAST)

[Static Application Security Testing](https://docs.gitlab.com/ee/user/application_security/sast/) is used to check source code for known security vulnerabilities and should be treated with equal, if not more importance than other types of software tests. GitLab offers built in SAST scanning functionality via GitLab CI/CD using the [semgrep analyzer](https://gitlab.com/gitlab-org/security-products/analyzers/semgrep).

:star: **Requirements:** :star:

- SAST scans must be run in the CI/CD pipeline.
- SAST scan results must contain no MEDIUM, HIGH, or CRITICAL vulnerabilities.
- False positives must be marked and [dismissed](https://docs.gitlab.com/ee/user/application_security/vulnerability_report/#dismiss-a-vulnerability) in the project's vulnerability report, with proper justification provided in the "description" field.

**Recommendations:**

- Integrate mitigating SAST scan results as part of development workflow.
- Check SAST scan results during development during every build to identify false positives early.

**Code Example:**

```
# Basic gitlab-ci.yml file including SAST scanning and report generation

stages:
- security-scan

include: Jobs/SAST.gitlab-ci.yml

sast:
  stage: security-scan
  artifacts:
    paths: 
      - gl-sast-report.json
    reports:
      sast: gl-sast-report.json
```
_[Back to the top](#devsecops-testing-requirements)_

### Dependency Scanning 

[Dependency scanning](https://docs.gitlab.com/ee/user/application_security/dependency_scanning/) analyzes project dependencies for knows security vulnerabilities. All dependencies utilized in a project are scanned, including transitive (nested) dependencies. GitLab offers built in dependency scanning functionality via GitLab CI/CD using the [gemnasium-python](https://gitlab.com/gitlab-org/security-products/analyzers/gemnasium) analyzer, supporting Pip, Pipenv and Poetry.

:star: **Requirements:** :star:

- Dependency scans must be run in the CI/CD pipeline.
- Dependency scan results must contain no MEDIUM, HIGH, or CRITICAL vulnerabilities.

**Recommendations:**

- Address dependency vulnerabilities as soon as possible and plan for time to test dependency verisioning compatibility. Changing the version of a dependency to address a vulnerability can often break compatibility across reliant dependencies and this may not be noticable until runtime.

**Code Example:**

```
# Basic gitlab-ci.yml file including dependency scanning and report generation

stages: security-scan

include:
- template: Jobs/Dependency-Scanning.gitlab-ci.yml

dependency_scanning:
  stage: security-scan
  artifacts:
    paths:
    - gl-dependency-scanning-report.json
    reports:
      dependency_scanning:
        - gl_dependency-scanning-report.json
```
_[Back to the top](#devsecops-testing-requirements)_
