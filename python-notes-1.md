# 🐍 Part 1: The Python Interpreter
<br/>

## Extensibility

Python is an extensible language, you can add new functions or modules in C to the interpreter, which allow you to
perform operations at a greater speed. You can also link to binary programs or libraries, or link the interpreter 
to an application written in C, using it as an extension for the application.
<br/>

## The interpreter

The interpreter is usually installed in `/usr/local/bin/python3.7`, if we have `/usr/local/bin` in our `$PATH` we can
start the Python 3 interpreter in the command line by typing the following:

```
$ python3.7 // Specifically for version 3.7
OR
$ python3
```

To exit the interpreter, type `ctr-D` (the EOF character) or write `quit()`

It is also possible to execute python code with the `-c` flag, followed by the code to execute, the quotes are optional 
but recommended to avoid any issues:

```
$ python -c 'print("hello")'
hello
```

Additionally, we can execute python modules as script files, using the `-m` flag:
```
---
my_module.py
greeting = 'hey'
print(greeting)
---

$ python -m my_module
hey
```

When we run a module or command, we can also enter interactive mode after it has finished, by using the `-i` flag:
```
$ python -im my_module
hey
>>> greeting
'hey'
```
<br/>

### Arguments

The interpreter can also receive a list of arguments which are assigned to the `argv` variable in the `sys` module.
This list contains a series of strings for the arguments passed, as well as the name of the script if provided 
(or an empty string if not).

```
$ python3
>>> import sys
>>> print(sys.argv)
['']
```

If the `-c` flag is used, then the first element of the list will be `'-c'`, and if the `-m` flag is used, it will be set
to the full name of the module:

```
$ python3 -c 'print("hello")'
hello
>>> import sys
>>> print(sys.argv)
['-c']

$ python3 -im my_module 3 4 test
hey
>>> import sys
>>> print(sys.argv)
['/Users/user/path_to_file/my_module.py', '3', '4', 'test']
```
<br/>

### Interactive mode

When in interactive mode, the interpreter will prompt for a _primary prompt_ with `>>>`. For continuation lines 
(indented), it will prompt for a _secondary prompt_ with `...`.

```
$ python3
>>>if 1 > 0:
...    print('1 is greater than 0')
...
1 is greater than 0
```
<br/>

## Encoding

By default, python 3 uses UTF-8 for the encoding of its source files. If we want to use a different encoding, 
we need to declare this at the top of the file.
<br/>

## Sources
[Python Docs tutorial - 1](https://docs.python.org/3/tutorial/appetite.html)<br/>
[Python Docs tutorial - 2](https://docs.python.org/3/tutorial/interpreter.html)

[Continue with Part 2: Basic types and operations](https://github.com/alysanne/python_notes/blob/master/python-notes-2.md)
