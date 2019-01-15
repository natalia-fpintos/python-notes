# 🐍 Part 4: Functions
<br/>

## Defining functions

We define new functions with the `def` keyword. If we wish to document our function, we can add a string literal 
as the first statement of the function, this is known as a `docstring` or documentation string. We can access the 
docstring calling `function_name.__doc__`:

```python
def add_two_nums(a, b):
  """This function adds two numbers (a and b) and prints the result of the adding operation."""
  print(a + b)
  
add_two_nums(5, 4)
9

print(add_two_nums.__doc__)
This function adds two numbers (a and b) and prints the result of the adding operation.
```
<br/>

## Functions and variable scope

When a function is executed, a new `symbol table` is created for it, containing all variables local to the function.
Therefore, all the variable assignments done inside the function will be saved in this table.

When we reference a variable inside a function, Python will first look for a variable with such name in:
  1. The `local symbol table` for the function
  2. Then in any `local symbol tables` for enclosing functions
  3. Then in the `global symbol table`
  4. Finally, in the `table of built-in names` 

For this reason, we cannot directly assign a value to a global variable inside a function (unless we name them in a 
`global` statement):

```python
x = 1

def change_x():
  x = 7
  print('local x is equal to {}'.format(x))

change_x()
print('global x is equal to {}'.format(x))

local x is equal to 7
global x is equal to 1
```

However, we can reference these global variables inside the function:

```python
x = 1

def print_x():
  print(x)

print_x()
1
```

Functions in Python can return a specific value with the `return` keyword. Othwerise, they will always return `None`:

```python
def add_two_nums(a, b):
  return a + b
 
def do_nothing():
  pass
  
print(add_two_nums(1, 3))
4

print(do_nothing())
None
```
<br/>

## Function arguments

The parameters of a function are added to the `local symbol table` for the function when it is called, these are passed by using __call by value__.

We can define a default value for an argument, which will be used if the function is called without a value for that argument:

```python
def say(something='Hello World!'):
  print(something)
  
say('Hey there!')
Hey there!

say()
Hello World!
```
<br/>

## Keyword arguments

When a function has arguments that are optional (have been defined with a default value), it's possible to define which is 
the argument keyword for the value being passed, in case we want to send arguments in a different order, or skip some:

```python
def say_greeting_and_name(greeting='Hey', name='friend', punctuation='!'):
  print('{}, {}{}'.format(greeting, name, punctuation))
  
say_greeting_and_name()
Hey, friend!

say_greeting_and_name('Good morning', 'sir', '.')
Good morning, sir.

say_greeting_and_name(punctuation='!!!', greeting='Hello there')
Hello there, friend!!!
```
<br/>

## Accessing all arguments and keywords

There are additional arguments that can be added to a function to provide additional functionality:

- An argument which starts with a single star `*`: this receives a tuple that contains all the arguments beyond 
the formal (defined) parameter list. This is helpful when we want to define a function that takes a __variable__ 
number of arguments.

```python
def printing_arguments(a, b, *args):
  for arg in args:
    print(arg)

printing_arguments('This is a', 'This is b', 'This is not a formal parameter', 'This one also isn\'t!')
This is not a formal parameter
This one also isn't!
```

- An argument which starts with two stars `**`: this receives a dictionary which contains the keywords and values for 
all arguments that follow the formal arguments.

```python
def printing_keywords(a, b, *args, **keywords):
  for keyword in keywords:
    print('{}: {}'.format(keyword, keywords[keyword]))

printing_keywords('This is a', 'This is b', c='This is c', d='This is d')
c: This is c
d: This is d
```
<br/>

## Packing and unpacking

Under the hood, the `*` and `**` are used to unpack tuples/lists and dictionaries, for example:

```python
list(range(1, 4))
[1, 2, 3]

# Unpacking the list to pass the values to range()
args_for_range = [1, 4]
list(range(*args_for_range))
[1, 2, 3]
```

```python
def say(greeting, name):
  print('{}, {}'.format(greeting, name))

# Unpacking the dict to pass the values to say()
my_args = {"greeting": "Hello", "name": "World!"}
say(**my_args)
Hello, World!
```
<br/>

## Lambda functions

We can create small anonymous functions with the `lambda` keyword. These are restricted to a single expression.

```python
pairs = [(1, 'b'), (2, 'c'), (3, 'a')]

# Sorting by the element in index 1
pairs.sort(key=lambda pair: pair[1])

[(3, 'a'), (1, 'b'), (2, 'c')]
```
<br/>

## Function annotations

It is possible to provide __annotations__ to a function, these specify an expression that can help document the function. 
These are optional and don't have any effect. We can access annotations with `function_name.__annotations__`.

Annotations can be provided for:
  - An argument: with a colon and an expression right after the argument.
  - The return value of a function: with an arrow `->` and an expression right before the colon that denotes the end of the
  `def` statement.

```python
def add_two(x: 'an integer', y: 'another integer') -> int:
  return x + y
  
print(add_two.__annotations__)
{'x': 'an integer', 'y': 'another integer', 'return': <class 'int'>}
```
<br/>

## Sources
[Python Docs tutorial - 4](https://docs.python.org/3/tutorial/controlflow.html)

[Continue with Part 5: Data structures](https://github.com/alysanne/python_notes/blob/master/python-notes-5.md)
