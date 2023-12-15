# Table of Contents

- [Table of Contents](#table-of-contents)
  - [License](#license)
  - [C/C++](#cc)
    - [X-Macros](#x-macros)
    - [Lambdas](#lambdas)
    - [C tipps](#c-tipps)
  - [bash script programming](#bash-script-programming)
    - [Debugging with set](#debugging-with-set)
    - [Strong Quoting with the Single Quotes](#strong-quoting-with-the-single-quotes)
    - [Weak Quotes with the Double Quotes](#weak-quotes-with-the-double-quotes)
    - [bash conditional expressions](#bash-conditional-expressions)
    - [$? and other special parameters](#-and-other-special-parameters)
    - [Return from function](#return-from-function)
    - [switch/case in bash](#switchcase-in-bash)
    - [while-loop is executed in a subbash](#while-loop-is-executed-in-a-subbash)
    - [regexp](#regexp)
    - [Linter](#linter)
  - [Java](#java)
    - [Compiling](#compiling)
    - [Applets](#applets)
    - [How do I get name of enum constant?](#how-do-i-get-name-of-enum-constant)
  - [Android](#android)
    - [Get shell acess to device](#get-shell-acess-to-device)
    - [Sqlite in android](#sqlite-in-android)
  - [XML](#xml)
    - [XSLT](#xslt)
  - [JavaScript \& node.js](#javascript--nodejs)
    - [Sandbox](#sandbox)
    - [npm](#npm)
    - [npm private registry](#npm-private-registry)
  - [Electron](#electron)
    - [electron forge](#electron-forge)
  - [CSS](#css)
  - [rust](#rust)
    - [Installation](#installation)
    - [rustup](#rustup)
    - [Toolchains](#toolchains)
    - [Additional information](#additional-information)
  - [python](#python)
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
  - [PHP](#php)
    - [Show installed modules](#show-installed-modules)
    - [Debugging](#debugging)
  - [flutter](#flutter)
    - [Commands](#commands)
  - [Qt](#qt)
    - [Scripting installer](#scripting-installer)
  - [plantUML](#plantuml)

## License

| Link                                      | Description                   |
| ----------------------------------------- | ----------------------------- |
| [1](https://habr.com/ru/articles/243091/) | A lot info about all possible |
| [2](https://habr.com/ru/articles/40293/)  | Shortly about most important  |
| [3](https://habr.com/ru/articles/284390/) | GPL                           |
| [4](https://habr.com/ru/articles/284394/) | BSD                           |
| [5](https://habr.com/ru/articles/459732/) | Apache2                       |

## C/C++

### X-Macros

The most common use of X Macros() is for associating error text with error codes. When new error codes are added, programmers must remember to add the code and the text, typically in separate places. The X Macro allows the new error data to be added in a single place and get automatically populated anywhere it is needed.

See further infos with examples on [Link](http://stackoverflow.com/questions/264269/what-is-a-good-reference-documenting-patterns-of-use-of-x-macros-in-c-or-possib)

### Lambdas

[Link](http://www.dreamincode.net/forums/topic/264061-c11-fun-with-functions/) And this one [Link](http://www.cprogramming.com/c++11/c++11-lambda-closures.html) are usefull

- []: no variables defined. Attempting to use any external variables in the lambda is an error.
- [x, &y]: x is captured by value, y is captured by reference
- [&]: any external variable is implicitly captured by reference if used
- [=]: any external variable is implicitly captured by value if used
- [&, x]: x is explicitly captured by value. Other variables will be captured by reference
- [=, &z]: z is explicitly captured by reference. Other variables will be captured by value
- [this]: Capture the this pointer of the enclosing class

### C tipps

[Some useful tipps](https://matt.sh/howto-c)

## bash script programming

[Guide](./Files/File%20Bash-Beginners-Guide.pdf)

### Debugging with set

- set -x - Causes bash to print each command before executing it.
- set -e - Exit immediately if a command exits with a non-zero status. Note that failing commands in a conditional statement will not cause an immediate exit.
- set -o pipefail - Sets the pipeline exit code to zero only if all commands of the pipeline exit successfully.
- set -u - Causes the bash bash to treat unset variables as an error and exit immediately.
- set -E - Improves handling ERR signals

### Strong Quoting with the Single Quotes

When you need to quote several character at once, you could use several backslashes:

```bash
echo a\ \ \ \ \ \ \ b
```

(There are 7 spaces between 'a' and 'b'.) This is ugly but works. It is easier to use pairs of quotation marks to indicate the start and end of the characters to be quoted:

```bash
echo 'a       b'
```

(The HTML ruins the formatting. Imagine that there are 7 spaces between the a and b. -Bruce) Inside the single quotes, you can include almost all meta-characters:

```bash
echo 'What the *heck* is a $ doing here???'
```

What the \*heck\* is a $ doing here???

The above example uses asterisks, dollar signs, and question marks meta-characters. The single quotes should be used when you want the text left alone. If you are using the C shell, the "!" character may need a backslash before it. It depends on the characters next to it. If it is surrounded by spaces, you don't need to use a backslash.

See further information on [Link](http://www.grymoire.com/Unix/Quote.html#toc-uh-1)

### Weak Quotes with the Double Quotes

Sometimes you want a weaker type of quoting: one that doesn't expand meta-characters like "*" or "?," but does expand variables and does command substitution. This can be done with the double quote characters:

```bash
echo "Is your home directory $HOME?"
Is your home directory /home/kreskin/u0/barnett?
```

```bash
echo "Your current directory is `pwd`"
Your current directory is /home/kreskin/u0/barnett
```

Once you learn the difference between single quotes and double quotes, you will have mastered a very useful skill. It's not hard. The single quotes are stronger than the double quotes. Got it? Okay. And the backslash is the strongest of all.

See further information on [Link](http://www.grymoire.com/Unix/Quote.html#toc-uh-2)

### bash conditional expressions

<img src="./Images/bash_condit_expressions.jpg" alt="drawing" width="400"/>

### $? and other special parameters

```bash
- $* bezeichnet alle Positionsparameter von 1 an. In Anfuehrungszeichen gesetzt, steht ``$*'' fuer ein einziges Wort, bestehend aus dem Inhalt aller Positionsparameter, mit dem ersten ``internen Feldseperator'' (meistens Leerzeichen, Tab und Zeilenende) als Trennzeichen.
- $@ bezeichnet alle Positionsparameter von 1 an. In Anfuehrungszeichen gesetzt, wird es durch die Werte der einzelnen Positionsparameter (jeweils ein einzelnes Wort) ersetzt.
- $# Anzahl der Positionsparameter
- $? Rueckgabewert (Status) des zuletzt ausgefuehrten Kommandos
- $- steht fuer die Optionsflags (von set oder aus der Kommandozeile).
- $$ Prozessnummer der bash
- $! Prozessnummer des zuletzt im Hintergrund aufgerufenen Kommandos
- $0 Name des bashscripts
- $_ letztes Argument des zuletzt ausgefuehrten Kommandos
- ${var%/*}  - Removes everything after the last occurrence of / - File path
- ${var##*/} - Removes everything up to the last occurrence of / - File name
- ${var##*.} - File extension
```

### Return from function

```bash
$(...) captures the text sent to stdout by the command contained within. 
return does not output to stdout. $? contains the result code of the last command
```

For getting of result use $?:

fun1 (){
  return 34
}

fun2 (){
  fun1
  local res=$?
  echo $res
}

### switch/case in bash

```bash
#!/bin/bash

eval set -- $(getopt -n $0 -o "-rvxl:" -- "$@")

declare r v x l
declare -a files
while [ $# -gt 0 ] ; do
        case "$1" in
                -r) r=1 ; shift ;;
                -v) v=1 ; shift ;;
                -x) x=1 ; shift ;;
                -l) shift ; l="$1" ; shift ;;
                --) shift ;;
                -*) echo "bad option '$1'" ; exit 1 ;;
                *) files=("${files[@]}" "$1") ; shift ;;
         esac
done

if [ ${#files} -eq 0 ] ; then
        echo output file required
        exit 1
fi

[ ! -z "$r" ] && echo "r on"
[ ! -z "$v" ] && echo "v on"
[ ! -z "$x" ] && echo "x on"
[ ! -z "$l" ] && echo "l == $l"

echo "output file(s): ${files[@]}"
```

### while-loop is executed in a subbash

It tooks some time for me to find why the variable value loosing [Link](https://unix.stackexchange.com/questions/402750/modify-global-variable-in-while-loop)

### regexp

| Link                                           | Description                        |
| ---------------------------------------------- | ---------------------------------- |
| [1](http://www.grymoire.com/Unix/Sed.html)     | Sed - An Introduction and Tutorial |
| [2](http://www.grymoire.com/Unix/Regular.html) | Regular Expressions                |
| [3](http://regex101.com/)                      | Testing of the regular expressions |

### Linter

For checking of script syntax can use this one [Link](https://www.shellcheck.net/) or use:

```bash
apt install shellcheck
```

## Java

### Compiling

For SW compiling use:

```bash
javac example.java
```

### Applets

I could't start applets because icedtea6-plugin was not installed. Here [Link](http://askubuntu.com/questions/84638/why-can-i-not-see-java-applets-in-firefox-8-on-ubuntu-10-04) I found solution how to fix this problem

I found some applets [here](http://www.jgiesen.de/javascript/Beispiele/Beispiele.html)

### How do I get name of enum constant?

This example demonstrate how to user enum‘s name() method to get enum constant name exactly as declared in the enum declaration. package org.kodejava.example.fundamental;

```java
 enum ProcessStatus {
   IDLE, RUNNING, FAILED, DONE;

   @Override
   public String toString() {
       return "Process Status: " + this.name();
   }
 }

 public class EnumNameDemo {
   public static void main(String[] args) {
       for (ProcessStatus ps : ProcessStatus.values()) {
           //
           // Gets the name of this enum constant, exactly as
           // declared in its enum declaration.
           //
           System.out.println(ps.name());
   
           //
           // Here we call to our implementation of the toString
           // method to get a more friendly message of the
           // enum constant name.
           //
           System.out.println(ps.toString());
       }
   }
 }
```

Our program result:
 IDLE
 Process Status: IDLE
 RUNNING
 Process Status: RUNNING
 FAILED
 Process Status: FAILED
 DONE
 Process Status: DONE

## Android

### Get shell acess to device

Install android-tools-adb packet using classical:

```bash
sudo apt-get install android-tools-adb
```

Then in console run:

```bash
adb kill-server 
sudo adb start-server
adb shell
```

For more information about using of adb visit [Link](http://developer.android.com/tools/help/adb.html)

### Sqlite in android

SQlite stores the whole database in a file. If you have access to this file, you can work directly with the data base. Accessing the SQlite database file only works in the emulator or on a rooted device. A standard Android device will not grant read-access to the database file.

Shell access to the database It is possible to access an SQLite database on the emulator or a rooted device via the command line. For this use the following command to connect to the device.

```bash
adb shell 
```

The command adb is located in your Android SDK installation folder in the "platform-tools" subfolder. Afterwards you use the "cd" command to switch the database directory and use the "sqlite3" command to connect to a database. For example in my case:

```bash
# Switch to the data directory
cd /data/data
# Our application
cd de.vogella.android.todos
# Switch to the database dir
cd databases
# Check the content
ls
# Assuming that there is a todotable file
# connect to this table
sqlite3 todotable.db 
```

The most important commands are:

| Command | Description                                                                             |
| ------- | --------------------------------------------------------------------------------------- |
| .help   | List all commands and options                                                           |
| .exit   | Exit the sqlite3 command                                                                |
| .schema | Show the CREATE statements which were used to create the tables of the current database |

## XML

### XSLT

XSL = XML Stylesheet Language XSLT = XSL Transformer / Translator

## JavaScript & node.js

Not bad tutorial website at [Link](http://javascript.ru)

Checking how your script works at http://jsfiddle.net/XssCG/244/

### Sandbox

[Link](https://www.w3schools.com/jquery/tryit.asp?filename=tryjquery_eff_slideup_slidedown)

### npm

Install developer version of chromium:

```bash
npm install --save-dev chromium
```

Install production version of chromium:

```bash
npm install --save chromium
```

Uninstall chromium:

```bash
npm uninstall --save chromium
```

Chromium will be installed in

~/node_modules/chromium/lib/chromium/chrome-linux

tips [Link](https://habr.com/ru/articles/133363/)

### npm private registry

Verdaccio, s. https://verdaccio.org/ and https://blog.bitsrc.io/how-to-set-up-a-private-npm-registry-locally-1065e6790796

Unset registry:

```bash
npm config delete registry
```

```bash
npm configs
npm config list
```

## Electron

### electron forge

Electron Forge is an all-in-one tool for packaging and distributing Electron applications Simple information at [Link](https://www.electronforge.io/)

## CSS

| Link                             | What for                                |
| -------------------------------- | --------------------------------------- |
| [1](https://fontawesome.com/)    | The Internet's icon library and toolkit |
| [2](https://materializecss.com/) | Frontend, CSS framework used for button |

## rust

### Installation

```bash
curl https://sh.rustup.rs -sSf | sh
```

### rustup

| Command                | What for                                                               |
| ---------------------- | ---------------------------------------------------------------------- |
| build                  | Building project. Could be combined with --verbose, --debug, --release |
| clean                  | Cleaning projec                                                        |
| install cargo-binutils | Install binutils                                                       |

### Toolchains

At start install arm toochain:

```bash
sudo apt-get install gcc-arm-none-eabi
```

[Link](https://rust-embedded.github.io/cortex-m-quickstart/cortex_m_quickstart/)

\* thumbv6m-none-eabi
\* thumbv7m-none-eabi
\* thumbv7em-none-eabi
\* thumbv7em-none-eabihf

Figure out the cross compilation target to use:
\* Use thumbv6m-none-eabi for ARM Cortex-M0 and Cortex-M0+
\* Use thumbv7m-none-eabi for ARM Cortex-M3
\* Use thumbv7em-none-eabi for ARM Cortex-M4 and Cortex-M7 (no FPU support)
\* Use thumbv7em-none-eabihf for ARM Cortex-M4F and Cortex-M7F (with FPU support)

### Additional information

| Link                                                                            | Description           |
| ------------------------------------------------------------------------------- | --------------------- |
| [1](https://www.rust-lang.org/what/embedded)                                    | Rust embedded         |
| [2](https://docs.rust-embedded.org/book)                                        | Embedded rust book    |
| [3](https://github.com/rust-embedded/wg)                                        | Some info             |
| [4](https://rurust.github.io/rust_book_ru)                                      | Russian book          |
| [5](https://docs.rust-embedded.org/book/c-tips/index.html)                      | Tipps for C developer |
| [6](https://doc.rust-lang.org/book/ch09-02-recoverable-errors-with-result.html) | Error handling        |

## python

### Exceptions

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

### Packages

I have at [Link](https://pypi.org/manage/account/)

with username velikS76 for velik76@googlemail.com

How to create package for pypi: https://packaging.python.org/en/latest/tutorials/packaging-projects/ Create files in described structure and then run this command from the same directory where pyproject.toml is located:

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

### flit

Also possible to use the [Link](https://flit.pypa.io/en/stable) for generating and publishing of packages

### coockiecutter

Creates the package template: [Link](https://github.com/audreyfeldroy/cookiecutter-pypackage)

### pip

```bash
sudo apt install python-pip
sudo apt install python3-pip
```

Or so:

```bash
python3 -m pip install --upgrade pip
python2 -m pip list
```

# venv

```bash
pip3 install virtualenv
```

### @ decorators

Uses the @ symbol to expand functionality as shown for example here [Link](https://builtin.com/software-engineering-perspectives/python-symbol)

This decorator:

- accepts operate() function as an argument.
- extends the function operate() by creating an inner function with the extended behavior.
- returns the inner() function—a new version of operate() function.

Further most used decorators:

- @property
- @classmethod
- @staticmethod

### unit tests

Unit testing in the Python extension is disabled by default. You must enable a test framework to run unit tests, and only a single test framework can be enabled at a time.

- Run the command Python: Configure Tests.
- Select the framework.
- Select the directory that contains the test.
- Select the pattern to identify test files.

### static code analyzer

Use for example mypy like:

```bash
mypy file.py --strict
```

Settings for vscode settings.json:

{
    "python.linting.mypyEnabled": true,
    "python.linting.enabled": true
}

### GUI

Nice lib https://github.com/hoffstadt/DearPyGui

## PHP

### Show installed modules

```bash
php -m
```

### Debugging

Can check the /var/log/apache2/error.log file and in php print out with error_log(), for example:

error_log("Sergey. Value: " . $value)

rrd in PHP

1. Install:

```bash
sudo apt install librrd-dev php-dev php-pear
```

2. May be need to config http-proxy with

```bash
pear config-set http_proxy localhost:3128
```

3. Install rrd extension for php with:

```bash
sudo pecl install rrd
```

4. Can use to get some info the

```bash
php-config
```

and

```bash
pecl list
```

5. In /etc/php/7.2/apache/php.ini/ insert the extension=rrd.so
6. Restart apache2

## flutter

### Commands

Use

```bash
flutter doctor -v
```

to check if it works ok. Use

```bash
flutter pub add flutter_form_builder
```

to add flutter-form-builder module, s. [Link](https://pub.dev/packages/flutter_form_builder)

## Qt

### Scripting installer

It uses controller scripting described in [Link](https://doc.qt.io/qtinstallerframework/noninteractive.html) Called with script and invalid proxy to prevent network access:

```bash
export https_proxy=1.2.3.4; sudo --preserve-env=https_proxy ./qt-opensource-linux-x64-5.12.8.run --script install_qt.qs
```

To get elements in widget call with logging in verbose mode like:

```bash
Controller.prototype.WelcomePageCallback = function() {
    var widget = gui.currentPageWidget();
    console.log(JSON.stringify(widget));
}
```

Some useful info at [Link](https://stackoverflow.com/questions/25105269/silent-install-qt-run-installer-on-ubuntu-server)

## plantUML

[Link](https://plantuml.com)

VSCode plugin https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml
