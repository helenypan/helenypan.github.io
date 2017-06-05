# sorted(list) vs. list.sort()

- **sorted()** returns a new sorted list, leaving the original list unaffected. 
- **list.sort()** sorts the list **in-place**, mutating the list indices, and **returns None** (like all in-place operations)
- **sorted()** works on any iterable, not just lists. Strings, tuples, dictionaries(you'll get the keys), generators, etc., returning a list containing all elements, sorted.
- use **list.sort()** when you want to mutate the list, **sorted()** when you want a new sorted object back.  
- use **sorted()** when you want to sort something that is an ietrable, not a list yet.
- for **lists**, list.sort() is faster than sorted() because it doesn't have to create a copy. For any other iterable, you have no choice.
- once you called **list.sort()**, the original order is gone. you cannot retrieve the original positions. 