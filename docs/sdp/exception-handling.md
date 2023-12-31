# Exception Handling Guidelines

Software exceptions can and do occur in all types of software products. Often they are unexpected and if not handled properly, at best they are a nuisance to the user and at worst can cause catastrophic system failures and data loss. This guide provides recommendations for how to use and handle exceptions in Python for the JATIC project.

In general, exceptions occur for exceptional reasons -- that is, unexpected behaviors that are not part of normal control flow of the software. Exception handling typically comes with a performance cost and should be kept out of the happy path. Additionally, readability is reduced with more indented code blocks and reasoning about how the code operates suffers when exceptions are used to skip through multiple call levels. Following are some examples of when to use and not use exceptions.

## Try, Except, and Finally

The Python `try`, `except`, and `finally` blocks comprise the main mechanism for catching and handling exceptions. Use the `try` block to encapsulate code that may raise one or more types of exceptions. Use the `except` block to handle the exception. Use the `finally` block to execute required code regardless of whether an exception was raised or not (e.g. to close a file or respond to an API). See the [Python documentation on errors and exceptions](https://docs.python.org/3/tutorial/errors.html) for details on syntax.

## Logging Exceptions

All unexpected exceptions should be logged using the applicable logging facility. (**TBD** Define the method of logging and link to it here.) Whether the program can continue to run normally or not, logging the exception is vital for debugging. Given a logging facility that provides log levels, exceptions should be logged with a `warning` level if execution can continue or an `error` level if it cannot.

Repeated logging of the same exception should be avoided to prevent filling up log files. For example, the same exception might be raised for many images of a dataset. In this case, a flag might be used to log the exception only once. The logging facility may provide an mechanism to throttle message and, if so, should be configured to do so.

## Use Exceptions for Unexpected Behavior

Exceptions are considered atypical. Only use exceptions to convey when something unexpected happened. For example, when a method is not implemented or when a case is not supported, like so:

```
class MyClass:
    def foo(self):
        raise NotImplemented()

    def provide_service(self, type):
        if type == "service 1":
            return self.service1()
        elif type == "service 2":
            return self.service2()
        raise ServiceNotProvided()
```

## Don't Use Exceptions for Control Flow

Using exceptions in place of good control flow is discouraged. However, one allowable case where the use of an exception to affect flow control is the handling of keyboard interrupts or other asynchronous events that interrupt execution. For example:

```
def input_handler():
    try:
        while True:
            wait_for_input()
            process_input()
    except KeyboardInterrupt:
        print("Goodbye!")
```

Sometimes deeply nested loops will raise an exception where `break` statements are ineffective. However, a better practice is to put the looping code in its own function and use a return statement. For example:

```
# Bad:
def run_algorithm():
    try:
        for x in range(1000):
            for y in range(1000):
                for z in range(1000):
                    if check(x, y, z):
                        raise Exception()
    except Exception:
        print("found it!")
    
    # Do some more stuff...

# Good:
def look_for_it():
    for x in range(1000):
        for y in range(1000):
            for z in range(1000):
                if check(x, y, z):
                    return True
    return False

def run_algorithm():
    if look_for_it():
        print("found it!")
    
    # Do some more stuff...
```

## Return Status from Functions where Appropriate

In some cases, it might be helpful for the caller of a function to know if the call completed as planned, partially completed, or failed altogether. Or perhaps the called function is asynchronous and waiting on more data. In cases like these, returning status can be a better approach than raising an exception for performance and readability. Two questions to consider when determining the best approach would be: are multiple return statuses likely? And, can the caller handle the returned status and do something reasonable? If the caller can't or won't do anything with the status, it's not helpful to return it. If something bad or unrecoverable happens in the called function, then raising an exception (preferably a custom defined one as defined below) is preferred.

## Catch Specific Exceptions

Never use an except block without an exception type. Doing so handles all exceptions -- not only those that may be expected but unexpected exceptions as well, potentially hiding errors in a misbehaving program. For example:

```
# Bad:
try:
    foo()
except:
    print("caught foo's exception")

# Good:
try:
    bar()
except SomeExpectedError:
    print("this is the exception I'm looking for")
```

## Avoid Handling Exceptions Silently

Handling an exception, but doing nothing with it is a code smell. If there really is no action to take, at a minimum use logging or some other output to indicate the exception occurred. In the rare event that even outputting a message is offensive, at least comment the code appropriately. For example:

```
# Bad
try:
    foo()
except FooError:
    pass

# OK
try:
    foo()
except FooError:
    # We can safely ignore this error because blah, blah, blah.
    pass

# Good
try:
    foo()
except FooError:
    logging.info("Ignoring expected FooError")
```

## Don't Ignore External Exceptions

Review the calls you're making to system and third-party libraries to understand potential sources of exceptions. Handling them appropriately makes the application less likely to crash and hence more user friendly. For example, when using file I/O be certain to handle pertinent exceptions:

```
try:
    with open("data.dat", "r") as file:
        process(file)
except FileNotFoundError:
    print("file not found")
except PermissionError:
    print("permission denied")
except IOError:
    print("unable to read from file")
```

## Top-level Exception Handling

Handling all unexpected exceptions at the top level can improve the user experience by providing meaningful information about and error rather than a cryptic stack trace, like so:

```
def main():
    foo()

if __name__ == "__main__":
    try:
        sys.exit(main())
    except Exception as e:
        if flags.dev:
            raise e
        print(f"We're sorry, the following error occurred: {e}. Please contact your system administrator for help.")
        if flags.debug:
            traceback.print_exc()
```

## Handling SystemExit

Handling the `SystemExit` exception must be done with care. Typically `SystemExit` is handled to finish cleaning up before a program ends. Unit tests checking exit codes require that the exception be re-raised. However, to bypass the unit test altogether, use `os._exit()`. For example:

```
# This code will be unit tested to check its exit code.
try:
    sys.exit(main())
except SystemExit as e:
    if something_bad_happened:
        os._exit(666)
    else:
        raise
```

## Custom Exceptions

Use custom exception classes to raise and handle application specific errors. Use the built-in Python exception classes when the semantics make sense (e.g. `ValueError` is a good choice when a function or method receives an inappropriate argument value). Per PEP-8, derive exception classes from `Exception` and not `BaseException`. See [PEP-8, "Programming Recommendations"](https://peps.python.org/pep-0008/#programming-recommendations) for the rationale. For example:

```
# Bad:
def foo(bar):
    if not isinstance(bar, Bar):
        raise Exception()

# Good:
def foo(bar):
    if not isinstance(bar, Bar):
        raise ValueError()

    if not bar.is_in_good_state():
        raise BarError("Bar object not ready")
```

See [PEP-8, "Exception Names"](https://peps.python.org/pep-0008/#exception-names) for details on exception naming. In general, they should be names like classes with a suffix of `Error` for exceptions that are truly errors.
