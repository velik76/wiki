# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Exceptions](#exceptions)
  - [Packages](#packages)
  - [flit](#flit)
  - [coockiecutter](#coockiecutter)
  - [pip](#pip)
  - [venv](#venv)
  - [@ decorators](#-decorators)
  - [unit tests](#unit-tests)
  - [static code analyzer](#static-code-analyzer)
  - [GUI](#gui)

## Exceptions

[Link](https://realpython.com/python-raise-exception)

```bash
BaseException
 ├── BaseExceptionGroup
 ├── GeneratorExit
 ├── KeyboardInterrupt
 ├── SystemExit
 └── Exception
      ├── ArithmeticError
      │    ├── FloatingPointError
      │    ├── OverflowError
      │    └── ZeroDivisionError
      ├── AssertionError
      ├── AttributeError
      ├── BufferError
      ├── EOFError
      ├── ExceptionGroup [BaseExceptionGroup]
      ├── ImportError
      │    └── ModuleNotFoundError
      ├── LookupError
      │    ├── IndexError
      │    └── KeyError
      ├── MemoryError
      ├── NameError
      │    └── UnboundLocalError
      ├── OSError
      │    ├── BlockingIOError
      │    ├── ChildProcessError
      │    ├── ConnectionError
      │    │    ├── BrokenPipeError
      │    │    ├── ConnectionAbortedError
      │    │    ├── ConnectionRefusedError
      │    │    └── ConnectionResetError
      │    ├── FileExistsError
      │    ├── FileNotFoundError
      │    ├── InterruptedError
      │    ├── IsADirectoryError
      │    ├── NotADirectoryError
      │    ├── PermissionError
      │    ├── ProcessLookupError
      │    └── TimeoutError
      ├── ReferenceError
      ├── RuntimeError
      │    ├── NotImplementedError
      │    └── RecursionError
      ├── StopAsyncIteration
      ├── StopIteration
      ├── SyntaxError
      │    └── IndentationError
      │         └── TabError
      ├── SystemError
      ├── TypeError
      ├── ValueError
      │    └── UnicodeError
      │         ├── UnicodeDecodeError
      │         ├── UnicodeEncodeError
      │         └── UnicodeTranslateError
      └── Warning
           ├── BytesWarning
           ├── DeprecationWarning
           ├── EncodingWarning
           ├── FutureWarning
           ├── ImportWarning
           ├── PendingDeprecationWarning
           ├── ResourceWarning
           ├── RuntimeWarning
           ├── SyntaxWarning
           ├── UnicodeWarning
           └── UserWarning
```

## Packages

I have at [Link](https://pypi.org/manage/account/)

with username velikS76 for velik76@googlemail.com

How to create package for pypi: [Link](https://packaging.python.org/en/latest/tutorials/packaging-projects/) Create files in described structure and then run this command from the same directory where pyproject.toml is located:

```bash
python3 -m build
```

The result will be stored in dist directory

For uploading package into pypi call:

```bash
pip install --upgrade twine
python3 -m twine upload --repository testpypi dist/*
```

Example for this case I found on [Link](https://www.youtube.com/watch?v=tEFkHEKypLI)

## flit

Also possible to use the [Link](https://flit.pypa.io/en/stable) for generating and publishing of packages

## coockiecutter

Creates the package template: [Link](https://github.com/audreyfeldroy/cookiecutter-pypackage)

## pip

```bash
sudo apt install python-pip
sudo apt install python3-pip
```

Or so:

```bash
python3 -m pip install --upgrade pip
python2 -m pip list
```

## venv

```bash
pip3 install virtualenv
```

## @ decorators

Uses the @ symbol to expand functionality as shown for example here [Link](https://builtin.com/software-engineering-perspectives/python-symbol)

This decorator:

- accepts operate() function as an argument.
- extends the function operate() by creating an inner function with the extended behavior.
- returns the inner() function—a new version of operate() function.

Further most used decorators:

- @property
- @classmethod
- @staticmethod

## unit tests

Unit testing in the Python extension is disabled by default. You must enable a test framework to run unit tests, and only a single test framework can be enabled at a time.

- Run the command Python: Configure Tests.
- Select the framework.
- Select the directory that contains the test.
- Select the pattern to identify test files.

## static code analyzer

Use for example mypy like:

```bash
mypy file.py --strict
```

Settings for vscode settings.json:

{
    "python.linting.mypyEnabled": true,
    "python.linting.enabled": true
}

## GUI

Nice lib https://github.com/hoffstadt/DearPyGui

