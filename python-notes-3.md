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

## Sources
[Python Docs tutorial - 4](https://docs.python.org/3/tutorial/controlflow.html)
