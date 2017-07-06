# re.match vs. re.search

- **re.match** is anchored at the beginning of the string. That has nothing to do with newlinews, so it is not the same as using **^** in the pattern.
- **re.search** searches the entire string, looking for a location where the regular expresson pattern produces a match, and return a corresponding **MatchObject** instance. Return **None** if no position in the string matches the pattern.
- if you need to match at the beginning of the string, or to match the entire string, use match, it is faster; otherwise, use search. 

```python
string_with_newlines = """something
someotherthing"""

import re

print re.match('some', string_with_newlines) # matches
print re.match('someother', 
               string_with_newlines) # won't match
print re.match('^someother', string_with_newlines, 
               re.MULTILINE) # also won't match
print re.search('someother', 
                string_with_newlines) # finds something
print re.search('^someother', string_with_newlines, 
                re.MULTILINE) # also finds something

m = re.compile('thing$', re.MULTILINE)

print m.match(string_with_newlines) # no match
print m.match(string_with_newlines, pos=4) # matches
print m.search(string_with_newlines, 
               re.MULTILINE) # also matches
```

# \1, \number
Matches the contents of the group of the same number. Groups are numbered starting from 1. For example, (.+) \1 matches 'the the' or '55 55', but not 'thethe' (note the space after the group). This special sequence can only be used to match one of the first 99 groups. if the first digit of number is 0, or number is 3 octal digits long, it will not be interpreted as a group match, but as the character with octal value number. 

```python
import re
# output is 'cat in the hat'
re.sub(r'(\b[a-z]+) \1', r'\1', 'cat in the the hat')
# output is 'the the'
re.search(r'(\b[a-z]+) \1','cat in the the hat').group() 

```

# group(), groups(), groupdict()
- group() expression returns one or more subgroups of the match

```python
>>> import re
>>> m = re.match(r'(\w+)@(\w+)\.(\w+)','username@hackerrank.com')
>>> m.group(0)       # The entire match 
'username@hackerrank.com'
>>> m.group(1)       # The first parenthesized subgroup.
'username'
>>> m.group(2)       # The second parenthesized subgroup.
'hackerrank'
>>> m.group(3)       # The third parenthesized subgroup.
'com'
>>> m.group(1,2,3)   # Multiple arguments give us a tuple.
('username', 'hackerrank', 'com')
```
- groups() returns a tuple containing all the subgroups of the match

```python
>>> import re
>>> m = re.match(r'(\w+)@(\w+)\.(\w+)','username@hackerrank.com')
>>> m.groups()
('username', 'hackerrank', 'com')
```
- groupdict() returns a dictionary containing all the named subgroups of the match, keyed by the subgroup name.

```python
>>> m = re.match(r'(?P<user>\w+)@(?P<website>\w+)\.(?P<extension>\w+)','myname@hackerrank.com')
>>> m.groupdict()
{'website': 'hackerrank', 'user': 'myname', 'extension': 'com'}
```