# Python notes 🐍 - Part 3

## If / elif / else

Python has `if`, `elif` and `else` statements for flow control. It does not, however, have a `switch` / `case` statement:

```python
x = 1
y = 2

if x > y:
  print('x is greater than y')
elif x < y:
  print('x is smaller than y')
else:
  print('The variables are equal')
  
x is smaller than y
```
<br/>


## For loops

The `for` loop in Python allows us to iterate over the items of a sequence, this sequence has to be an iterable, such as a
`list` or a `string`.

```python
my_cats = ['Luli', 'Lula', 'Lily']

for cat in my_cats:
  print('I have a cat named {}'.format(cat))
  
I have a cat named Luli
I have a cat named Lula
I have a cat named Lily
```

__NOTE:__ Modifying the iterable during the `for` loop execution will change the number of iterations, as it will not make 
a copy. This can lead to infinite loops. It's recommended to make a copy of the iterable if we need to amend it, this will 
prevent this behaviour. We can achieve this with a slice:

```python
for cat in my_cats:
  # Do something
  
# Vs.

for cat in my_cats[:]:
  # Do something, using the slice
```
<br/>

## Ranges

The `range` function returns an iterable range, providing an sequence of numbers in arithmetic progression. The number 
passed as the end of the sequence will never be included as part of it. It is also possible to define a third parameter 
known as the `step`, the numbers to skip each time.

__NOTE__: The example below uses the `list` function to convert the range to an array

```python
list(range(5)) 
# [0, 1, 2, 3, 4]

list(range(3, 8)) 
# [3, 4, 5, 6, 7]

list(range(-10, 0, 3)) 
# [-10, -7, -4, -1]
```
<br/>

## Break, Continue and Else

Loops can have a `break` clause when we want to exit the loop before it has ended, and a `continue` clause when we 
want to skip the rest of the lines of the loop and continue with the next iteration.

```python
my_cats = ['Luli', 'Lula', 'Lily']

for cat in my_cats:
  if cat == 'Lula':
    break
  print('I have a cat named {}'.format(cat))
  
I have a cat named Luli
# Loop ended when it reached the second cat
```

```python
for cat in my_cats:
  if cat == 'Lula':
    continue
  print('I have a cat named {}'.format(cat))
  
I have a cat named Luli
I have a cat named Lily
# Loop skipped the second cat
```

Additionally, `for` and `while` loops can also have an `else` clause, this will be executed when the loop finishes 
its execution, except if it finished because of a `break` clause.

```python
for cat in my_cats:
  if cat == 'Lilian':
    break
  print('I have a cat named {}'.format(cat))
else:
  print('I printed all my cats!')
  
I have a cat named Luli
I have a cat named Lula
I have a cat named Lily
I printed all my cats!
# Loop finished without breaking and executed the else body
```
<br/>

## The pass statement

The `pass` statement does nothing, it's meant to be used when we need to define a statement but we don't really
want to do anything at the moment (for example when we create a function but still haven't coded its body.

```python
if 1 > 2:
  # Do something
```
^^^ This would error and require a statement.

The solution would be:
```python
if 1 > 2:
  pass
```
<br/>

## Defining functions

We define new functions with the `def` keyword. If we wish to document our function, we can add a string literal 
as the first statement of the function, this is known as a `docstring` or documentation string.

```python
def add_two_nums(a, b):
  """This function adds two numbers (a and b) and prints the result of the adding operation."""
  print(a + b)
  
add_two_nums(5, 4)
9
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

## Sources
[Python Docs tutorial - 4](https://docs.python.org/3/tutorial/controlflow.html)
