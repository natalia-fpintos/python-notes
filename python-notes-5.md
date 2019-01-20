# 🐍 Part 5: Data structures
<br/>

## Lists

Lists have many methods to manipulate them:

* `append`: adds an item at the end of the list.

* `extend`: adds an iterable at the end of the list.

* `insert`: adds an item at a given position in a list.

* `remove`: removes the first matching item in a list.

* `pop`: removes an item at a given position and returns it, by default removes and returns the last item.

* `clear`: removes all items from a list.

* `index`: returns the index of a matching item in a list, otherwise returns a ValueError.

* `count`: returns the number of times an item appears in a list.

* `sort`: sorts a list.

* `reverse`: reverses the items of a list.

* `copy`: returns a shallow copy of the list.

__NOTE:__ A shallow copy is a copy where we duplicate as little as possible. 
If we get a shallow copy of a list, we will get a new list, but the elements will be references to the elements that exist
in the original list. This allows us to quickly obtain a copy of the array, which we can manipulate (add, filter, remove 
elements) without modifying the original list.
<br/>

## Stacks and Queues

Lists can be used as stacks or queues:

* __Stacks:__ using a list as a stack (last in, first out) can be very convenient using the methods `append` and `pop`.
* __Queues:__ using lists as queues (first in, first out), however, is not so convenient, as appending or popping elements 
at the beginning of a list means shifting all the other elements in the list as well. It's better to implement queues with 
`collections.deque` instead, which provide fast inserts and pops from the beginning or end.
