### **Local, global and Non-local Variables**

In many functions, we have to define variables in the form of global , local or non-local. unknowingly we have used them in the programs. 

The variables which are defined outside the functions are known as <mark style="background: #ABF7F7A6;"><u>global variables</u></mark>. The scope of the global variable will be the entire program body below it..

The variables defined inside the functions are known as <mark style="background: #ABF7F7A6;"><u>local variables</u></mark>. They can also be accessed and defined by using  keyword /command `global`. Not accessible outside the function. Value is contained only inside the function.

To define non-local variables, we use `non local` keyword. Defined locally but are available to use throughout the function.

#### Local Variable

```python
def func1(num2):
	num1 = 1
	print(num1)
	print(num2 + num1)
func1(12)
print(num1)                #shows error since `num1` is a local variable and is                                 not available outside `func1()`
```

```python
def foo():
	y = "local name"
foo()
print(y)                    ##shows error since `y` is a local variable and is                                 not available outside `foo()`
```

```python
y = "global"
def foo():
	y = "local name"
foo()
print(y)                 #output will be `global` 
```


#### Global Variables

```python
g1 = 1 #G1
def display():
	l1 = 2 #G2
	print(l1)  #G3
	print(g1)  #G4

display()

print(g1)  #G5
print(l1)  #G6   # Output error for this line since it's a local variable and                         called outside it's scope
```

```python
g1 = 1
def display():
	g1 = 2
	print(g2)
	print("inside", id(g1))    #`id()` is an inbuilt function
display()
print(g1)
print("outside", id(g1))
```

 
   



