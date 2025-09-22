
```python
def <function_name>(parameters!optional!):
	""" docstring """
	statements
```


The built in functions are also known as <mark style="background: #FFB8EBA6;">pre-defined functions</mark>. It is already available in the python packages.
For e.g. :- ,`reversed()`,`input()`, `char()` are built in functions.


The functions which are defined by the programmer or the user to perform a specific task is known as <mark style="background: #FFB8EBA6;">user defined function.</mark>
Generally user defined function is written to avoid repetition. For e.g. :- my_av(), greet() is a user defined function.


##### POSITIONAL ARGUMENTS:-

```python
my_list = [5,3]
printf=(pow(*my_list))
my_tuple = (3,4)
print(complex(*my_tuple))

import math
my_set = 4
print(math.sqrt(*my_set))
```

##### KEYWORD ARGUMENTS:-

```python
def my_complex(my_real,my_imag):
	my_result = complex(my_real,my_image)
	return my_result
print(my_complex(my_real = 2,my_imag = 8))   #All produce same results.
print(my_complex(my_imag = 8,my_real = 2))
print(my_complex(2,my_imag = 8))
```

```python
def my_complex(my_real,my_imaginary):
	my_result = complex(my_real,my_image)
	return my_result
print(my_complex(2,8))  
```

 *Position does not matter if variables are included in the argument.*  

##### DEFAULT ARGUMENTS

```python
def my_details(name,age):
	printf(f"My name is {name} and age is {age} ")

def my_details1(name, age =31):
	print(f"My name is {name} and age is {age} ")

my_details('Mukesh', 31)               #D1
my_details(name = 'Mukesh')            #D2
my_details('Ramesh', 32)               #D3
```

```python
def my_details2(age = 31, name):
	print(f'my name is {name} and age is {age}')
```


##### VARIABLE LENGHT ARGUMENTS:-

Many a times while executing big projects, we will now know in advance, the number of arguments which will be passed into a function. So in python, there i something called the variable length arguments, that can accept any number of values. An asterisk `*` symbol is used before the parameter name to denote the preceding arguments.

Variable number of arguments can be passed to a function by using special syntax `*args`.
All the values are represented in the form in form of tuple. The number of arguments here will not be maintained.

```python
def mymul(*my_num):
	myresult = my_num[0]*my_num[1]*my_num[2]
	return myresult

def mymul2(first , *my_num):
	myresult = first*my_num[0]*my_num[1]
	return myresult

def mymul3(*my_num):
	myresult = 1
	for loop in my_num:
			myresult *= loop
	return myresult

print(mymul(2,3,4))                   #V1
print(mymul(2,3,4,5))                 #V2
print(mymul2(2,3,4))                  #V3
print(mymul2(2,3,4,5))                #V4
print(mymul3(2,3,4,5))                #V5
```



```python
def func1(**kwarg):
	print(kwarg)             #F1
	print(type(kwargs))      #F2
	for my_key, my_value in kwargs.items():
		print(f"my_key:my_value")          #F3

def func2(name1, **kwargs):
	print(kwargs)             #F4
	print(name1)              #F5
	print(type(kwargs))       #F6
	for my_key, my_value in kwargs.items():
		print(f"my_key:my_value")          #F7 

def func1(**kwarg):
	for my_key, my_value in kwargs.items():
		print(f"my_key:my_value")          #F9


func1(fname = "Saurabh", lname = "chandrakar", phone_number = 7249670699)    #F10
func2(1,fname = "Priyanka", lname = "chandrakar", phone_number = 7321546879)

#dictionary unpacking

d1 = dict(name = 'Saurabh', age = 31)

func3(**d3)
```


## Nested Functions

```python
def outside_func():
	def inner_func():
		print("Inside Inner Function")
	print("Inside Outer Function")
	inner_func()
outside_func()        #IF this line doesnt exist, then the whole outside                                  function(and hence the inner fucntions) will not run.
```

In the preceding program, `inner_func()` is defined inside `outer_func`, 



We can also pass a parameter to the function.

```python
def outside_func(str1):
	def inner_func():
		print(str1+"Inside inner function")
```


WE can also change variable of the outer function from inside the inner function.

```python
def outer(a):
	b = 3
	b =+ a          #b=b+a
	def inner(c):
		b = 6
		print(b**c)
	print(b)
	inner(3)
outer(6)
```


