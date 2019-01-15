# 🐍 Part 2: Basic types and operations
<br/>

## Basic operations

Integers have a type of `int`, while numbers with a decimal point have a type of `float`.
Any operation that includes a number with a decimal point will return a decimal point result.

Division with `/` always returns a `float`. If we divide with `//` we are doing a floor division and will get an 
integer, discarding the decimals.

We can calculate a modulo with `%`, and we use `**` to calculate a power.
<br/>

## Variables

We assign values to variables with the `=` sign.
Trying to access a variable that has not been assigned returns a `NameError` exception.

```python
>>> undefined_variable
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'n' is not defined
```
<br/>

When in interactive mode, we get a variable with the name of `_`, this one is assigned the value of the last 
printed expression. Be careful not to explicitly assign a value to it, it's read-only and re-assigning will 
create an independent local variable that would override it.

```python
>>> 3 + 4
7
>>> 3 + _
10
```
<br/>

## Strings

Strings can be defined between single or double quotes, it's possible to use `\` to escape a character inside them.
If we want the string to interpret backslashes as a character rather than used to define an escaped character, we can
use _raw strings_ by placing an `r` before the string:

```python
print('C:\name')
C:
ame

print(r'C:\name')
C:\name
```

We can also make strings span multiple lines with string literals, strings enclosed in triple quotes `"""` or `'''`.
These contain all the new lines used when writing the string, unless escaped with a `\`:

```python
>>> stringWithNewLines = """
... hi
... """

>>> stringWithNewLines
'\nhi\n'

>>> stringNoNewLines = """\
... hi\
... """

>>> stringNoNewLines
'hi'
```

We can concatenate strings with `+`, and also repeat them in a same string with `*`:

```python
myString = 'hi' + '!' * 3
print(myString)
hi!!!
```

It is also possible to concatenate strings when they are next to each other, but only if they are strings.
Variables or expressions with strings cannot be concatenated:

```python
python = 'py' 'thon'

myLongString = ( 'This is'
                  'a long string'
)
```
<br/>

### String indexation

We can access the characters of a string (which are also strings of size 1) with square bracket notation.
This can be done with positive indices starting from 0, and also with negative indices, starting from -1:

```python
python = 'python'

print(python[2])
t

print(python[-2])
o
```
<br/>

## String slicing

It is also possible to use the square bracket notation to slice strings and get a substring.
We would pass the first and last character (excluded) that we want to retrieve, separated by a colon.
Omiting the first number means that we want to retrieve characters from the beginning, and omitting the
last number means that we want to retrieve chatracters until the end.

```python
python = 'python'

print(python[:2])
py

print(python[2:])
thon

print(python[2:4])
th
```

If we try to access an index that is not available in the string, we will get an `IndexError`. However, using
indices that are too big or too small when slicing, doesn't throw an error.

```python
python[42]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: string index out of range

python[2:42]
thon
```

Also, strings are immutable, so we cannot reassign characters of it. If we want to change a string, we need to
create a new one.
<br/>

## Lists

Python lists are like arrays, they can contain many items, of the same or different types.
Such as with strings, we can also slice and access elements of a list with bracket notation.

```python
myList = ['p', 'y', 't', 'h', 'o', 'n']

print(myList[2:4])
['t', 'h']
```
<br/>

## Sources
[Python Docs tutorial - 3](https://docs.python.org/3/tutorial/introduction.html)

[Continue with Part 3: Control flow tools](https://github.com/alysanne/python_notes/blob/master/python-notes-3.md)
