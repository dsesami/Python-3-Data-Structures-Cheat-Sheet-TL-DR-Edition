# Python 3 Data Structures Cheat Sheet: TL;DR Edition
#### Originally written by Daniel Sami (https://github.com/dsesami)

A short reference for data structures in Python 3.x.
This page assumes you understand what these data structures are and when to use them
(or...not use them). Also assumes you know not to do things like modifying collection ranges
when iterating and stuff like that.
If you want more detail, check out the [official docs](https://www.python.org/doc/).

Complaints? Opinions? Additions? Feel free to make a pull request.

## General reference
```
len(foo) # length of collection
sorted(foo) # returns a sorted version (with dictionaries, sorts keys)
if element in foo: # checks if element is in in foo (with dictionaries, checks the keys)
for i in foo: # iterates over collection (with dictionaries, iterates over keys)
```

## How do I use a...?
#### List
Ordered, simple, they're arrays, we've all done this before.
```
foo = []
foo = list()
foo = ['a', 'b', 'c']

foo[0] # returns 'a'
foo[2] = x # changes the list to ['a', 'b', x']
foo.append('d') # add to end of list

foo.pop() # returns 'd' and removes it from the list.
foo.pop() # returns 'x' and removes it from the list.
```
#### Dictionary
These don't guarantee order in Python 3.
```
foo = {}
foo = dict()
foo = {
    'a': 1,
    'b': 2,
    'c': 3
}
foo['b'] # returns 2
foo['d'] = 4
foo.pop('d') # returns 4 and deletes that key-value pair from the dictionary. 

for element in foo: # iterates but only gives you keys. have to access value with foo[element]
for k, v in foo.items() # iterates and gives you keys and values.
```
#### Tuple
These are ordered and also immutable, FYI.
```
foo = ('x',) # need the comma if only one element is present
foo = ('x', 'y', 'z')
foo[1] # returns 'y'

```
#### Set
Unordered, good for random insertion and deletion.
```
foo = set() # only way to do empty sets because it uses brackets like dicts
foo = {'x', 'y', 'z'}

foo.add('a') # use this for one element
foo.update(['a', 'v', 'q']) # use for multiple elements, have to pass an iterable

foo.remove('x') # doesn't return anything
foo.pop('y') # returns 'y' and removes it from the set
foo -= {'z', 'bar'} # removes 'z' and 'bar' from the set (if they exist in there already)

foo.clear() # empties set
```
#### Stack / Queue
There's a ton of collections but try to keep it simple when you can.
For a stack, you can just use a list (queues aren't very fast in this form):
```
foo = []
foo.append('alpha')
foo.append('beta')
foo.pop() # returns 'beta'
```
Or, if you prefer, use the deque (double-ended queue) collection for stacks,
as well as queues. Just append/push or pop/remove as you need from either end.
```
from collections import deque

foo = deque()
foo = deque([], maxlen=10) # won't ever be bigger than 10 items
foo = deque('a', 'b', 'c')

foo.append('x') # add to end
foo.pop() # remove from end

foo.appendleft('x') # add to beginning
foo.popleft() # remove from beginning
```

Note: Built-in functions for data structures also work as conversion functions. 
`set('xyz')` and `set(['x', 'y', 'z'])` would both create a set
that looks like `{'x' 'y', 'z'}`.

