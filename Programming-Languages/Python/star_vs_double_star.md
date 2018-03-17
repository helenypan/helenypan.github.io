# * and **
The names ***args** and ****kwargs** are only by convention but there's no hard requirement to use them. (** is for a dictionary of keyword arguments)

- you would use ***args** when you are not sure how many arguments might be passed to your function, i.e. it allows you pass an arbitrary number of arguments to your function.

```python
def print_everything(*args):
	for count, thing in enumerate(args):
		print('{0}. {1}'.format(count, thing))

print_everything('apple', 'banana', 'cabbage')

output:
0. apple
1. banana
2. cabbage
```


- Similarly, ****kwargs** allows youto handle named arguments that you have not defined in advance:

```python
def table_things(**kwargs):
	for name, value in kwargs.items():
		print('{0} = {1}'.format(name, value))

table_things(apple="fruit",cabbage="vegetable")

output:
apple = fruit
cabbage = vegetable
```

- You can use these along with named arguments too. The explicit arguments get values first and then everything else is passed to ***args** and ****kwargs**. The named arguments come first in the list:

```python
def table_things(titlestring, **kwargs)
```
- You can also use both ***args** and ****kwargs** in the same function definition, but ***args** must occur before ****kwargs**. 

```python
class Handler(webapp2.RequestHandler):
    def write(self, *a, **kw):
        self.response.out.write(*a, **kw)
```

- You can also use the * and ** syntax when calling a function:

```python
def print_three_things(a,b,c):
	print('a={0}, b={1}, c={2}].format(a,b,c))

mylist =  ['aardvark', 'baboon', 'cat']
print_three_things(*mylist)

outout:
a = aardvark, b = baboon, c = cat
```
As you can see in this case, it takes the list(or tuple) of items and unpacks it. By this it matches them to the arguments in the function.

- You could have a * both in the function definition and in the function call.
- One place where the use of ***args** and ****kwargs** is quite useful is for subclassing, this way you can extend the behaviour of the Foo class without having to know too much about Foo. This can be quite convenient if you are prgramming to an API which might change. MyFoo just passes all arguments to the Foo class.

```python
class Foo(object):
	def __init__(self, value1, value2):
		print value1, value2

class MyFoo(Foo):
	def __init__(self, *args, **kwargs):
		print 'myfoo'
		super(MyFoo, self).__init__(*args, **kwargs)
```
