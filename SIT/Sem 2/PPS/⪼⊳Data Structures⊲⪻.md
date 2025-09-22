s
We will  learn about the following:-

-  [[|List data structure]]
- Tuple data structure
- Set data structure
- Dictionary data structure

# Lists

^0461d5

- Can store different types of elements. It represents a group of elements.
- Heterogeneous objects are allowed.
- Dynamic in size, as it can be increased or decreased as per our requirements.
- Elements of lists are mutable.
- Duplicate objects are allowed.
- Insertion order is preserved by using index.
- Duplicate objects are differentiated on the basis of index in a list.
- Lists are ordered.

The syntax of list creation is  as follows

```python
listname =[element1,element1,element1,element1]
```

For example:-

```python
my_fav_desserts = ['Cookies','Cake', 'Ice Cream']
my_num = [3, 5, 2, 8, 4, 5, 4, 3, 3]
robot_answers = [True, False, False, True, True]
```

When we creating a list, we not only storing not only a collection of objects, but also their order as well. This is how we access  a list's items.

### Creating an Empty List

Syntax

```python
listname =[]
```

For example

```python
myl1 = []
print(myl1)
print(type(myl1))
```

### Creating a list with Dynamic input

```python
mylist = eval(input("Enter the list: "))
print(mylist)
print(type(mylist))
```

### Creating a list with `list()` function

for the given sequence, we can provide either set, string , range and so on...

```python
mylist = list(range(1,10,2))
print(mylist)
print(type(mylist))
```

### List Creation using `split()` function

```python
st1 = "Fushiguro Toji"
mylist = (st1.split(' '))
print(mylist)
print(type(mylist))
```

<span class="cloze-span">
`output
['Nilesh', 'Bhaskarrao', 'Bahadure']`
</span>
^ayush
### Mutability of lists

Once we create a list, we can add new objects, delete existing ones and move objects around. Data types like string, integers, float, tuple and Boolean are unable to do so.

The position number of a list element will be represented by an index. The index will be written inside square brackets and starts from 0 onwards.

```python
more_Citrus_fruits = ["orange", "GrapeFruit", "Lemon", "Pomelo", "Lime"]
more_Citrus_fruits += ["brownies", "Muffins", "Chocolates"]

print(more_Citrus_fruits )
```

```python
myl1 = [11, 12, 13, 14]
print(myl1)
myl1[1] = 20                           #Changed Elements Using Index.
print(myl1)
```

```python
myl1 = [10, 20, -30.1, "Hello"]

print(myl1[3])
print(myl1[-1])
print(myl1[4])
```



## Basic commands for lists.

`len(list)` - Length of list.

`max(list)` - maximum value of the list

`min(list)` - minimum value of the list.

`list(sequence)` - converts the input sequence into list, including the space too.

`l.append(x)` - 'l' -> variable name. Appends 'x' to the end of list 'l'

`l.extend(x)` - extends original list with another list.

`l.insert(i,x)` - i -> index, inserts 'x' element in the 'i' index.

`l.remove(x)` - removes 'x' in list 'l', if duplicate items , removes only first

`l.pop(i)` - if index is not mentioned, the last indexed item is removed. Works on the                                concept of 'Last in First out'

`l.count(x)` - count of repeated items in list

`l.sort` - sorts in ascending order. If strings are in the list, then will sort will be based on                         ASCII value.

`l.index(x)` -  gives the index value of element 'x'

`l.reverse` - the entire content will be reversed

`del list` - complete list will be deleted. If index value is listed then the respective item will                      be deleted.



## List Comprehension

Offers a convenient way to produce new lists by performing an operation on each element on the existing list, these new lists are generated.

```python
num =
cube
for x in num:
	cube.append(x**3)
print(cube)
```

```python
myl1 = []
for a in range(4,6):
	for b in range (3,5):
		myli.append(a*b):
print(myl1)
lic1 = [a*b in range(4,6): for b in range (3,5): ]
print(lic1)
```


---

# Tuples

- Once we create a tuple object, no changes are being performed on object.
- We can find items within a tuple.
- Tuple cannot be appended or extended.
- For a single value , parenthesis are optional but must end with a comma.
- Elements can be of same data types or different.

```python
i1 = (20)                      #integer
print(i1)
print(type(i1))

i1 = (20,)                      #tuple
print(i1)
print(type(i1))
```


Using `tuple()`, an object can be converted to a tuple.

```python
l1 = [1,2,3,4]
print(tuple(l1))
print(type(tuple(l1)))

t2 = tuple(range(1,9,2))
print(t2)
```


Accessing the elements of Tuple:-

Using Index:

```python
myt1 = (10,20,-30.1, 'Hello')
print(myt1[3])
print(myt1[-1])
print(myt1[4])
```

Using for loop and Index:

```python
myt1 = (10,20,-30.1, 'Hello')
t_len = len(myt1)

for loop in range(t_len):
	print(loop, myt1[loop])

```

Using while loop and Index:

``` python
myt1 = (10,20,-30.1, 'Hello')
t_len = len(myt1)
count = 0

while count<t_len>
```

By Slicing:-
```python
myt1 = (10,20,-30.1, 'Hello', 34.1, True)
#displaying tuple
print("myt1", myt1)
#diffenrent slices:-
print("myt1[:4] ", myt1[:4])
print("myt1[1:] ", myt1[:1])
print("myt1[3:5] ", myt1[3:5])
print("myt1[::-1] ", myt1[::-1])
```


### Tuple vs Immutability:-

The tuple comprehension is not supported  in python. We will be getting an generator object instead of tuple object. Generator expression will  be producing one item at a time.

```python
g1 = (x**2 in range (0,6))

```


---

# Set

- Unordered collection of items.
- The elements may not appear in the same order as they were entered
- Insertion order is not preserved but <mark style="background: #CACFD9A6;">items can be sorted</mark>.
- There is no provision for indexing and slicing for the set.
- Once a set object is created, any changes can be performed in that object based on need. 
- Different values are allowed in the set.
- Sets are used to avoid duplicity.
- Sets are mutable.
- Enclosed in `{}`

```python
mys1 = det(range(1,10))
print(mys1)

mys2 = set('python')
print(mys2)

myl1 = [1,2,3,1,4,5]
mys3 = set(myl1)
print(mys3)

myd1 = {'a' :1, 'b':2, 'c': 3}
mys4 = set(myd1)
print(mys4)
```


- An empty set can be created using `set()` function.

```python
d1 = {}
print(d1)
print(type(d1))      #defaulted to dictionary instead of sets
```

## Set comprehension


```python
mys1 = set()
for loop in range(11):
	if loop%2 == 0:
		mys1.add(loop**3)
	else:
		mys1.add(loop**2)
print(mys1)



```

```python
mys1 = set()
for loop in range(21):
	if loop % 3 == 0:
		if loop % 4 == 0:
			mys1.add(loop**2)

print(mys1)
```

```python
mys1 = set(range(1,10))
print(mys1)

mys2 = set("python")
print(mys2)

myl1 = [1,2,,3,4,5]
mys3 = set(myl1)
print(mys3)

myd1 = {'a' : 1, 'b' : 2, 'c': 3}
mys4 = set(myd1)
print(myd1)
```

---

# Dictionary

^52ae49

- Used to show group of objects as key-value pair.
- Duplicate keys are not allowed, but values are.
- For both key and value, heterogenous objects are allowed.
- Insertion order is not preserved.
- Unordered collection, is mutable.
- Slicing and indexing are not allowed.
- If same key is mentioned again, then old key is overwritten
- Keys should be immutable.

Empty dictionary can be created using:-

```python
d1 = dict()
print(d1)
print(type(d1))
```

```python 
#syntax
d1= {'Key' : Value, 'Key' : Value , 'Key', Value}

d2= {
	 1: 'python'
	 2: 'is'
	 3: :'true'
	}
```

 