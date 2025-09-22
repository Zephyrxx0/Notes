## Algorithm

It is an systematic approach to define the problem accordingly.
E.g. :- TO device auto stopping mechanism in a vehicle based on the surroundings
	 the solution to the above problem can be implemented by integrated censor and a piece of code


Algorithm is a set of sequence used for performing a certain operation with having inputs and outputs.

E.g. An Automatic vehicle stop. Input is taken from the sensor and the output is through the   brakes. 

After processing  the processor gives command to the anti braking system to stop the vehicle

---
# Functions

Python consists of built in commands, for eg:- max, min , shortage, etc. Apart from this it i also possible user can define  their own commands. This commands is written using functions.

In short, function allows, user to define their own commands. For eg:- The built in command max will replace by a user defined command maximum.
The syntax of function of given below.

```python

`def <function_name>(): 
	`statement 1
	`statement 2
	`statement 3`
```

More in [[⩸Functions in Python⩸]]

---


#####  Ques) Write a function to find maximum of two numbers.  Give the name maximum to the function.

 Solution)  ```
```python
define maximum(a,b):
			 if a>=b:
				 largest = a
			 else:
				 largest = b

			print(largest)
maximum();

```

'string'
"string"
'''docstring'''

---

# ***Pseudo Code***

It is also known as dummy code. This is a set of instructions or commands executed by compiler or interpreter or assembler and not by the programming languages. No memory consumed by the pseudo instructions and hence it is also known as dummy instructions.

There is no standard syntax for the pseudo code and it is not machine readable. 

Common keywords used in pseudo code, 

START
END
BEGIN
IMPORT
READ
OUTPUT
PRINT
DISPLAY
WHILE
FOR
ENDFOR
IF
ELSE
ENDIF

---
# *Flow Control*



The flow of program can be changed using conditional statements. The regular syntax is stop and the program will jump on specified section. This process  is know as flow control or the programming is known as conditional programming.

For e.g.:- In a traffic light program, the user will visualize the signal condition, and if its green, the vehicle is allowed to pass, otherwise stop.

In day to fay life, we'll also experience the same situation and we need to select one among many for e.g.; - we have choices in vegetables, choices in fruits, and we need to decide one according to our preferences. 

In the conditional statement, following topics are important, 

1) Flow of execution of the program
	1) Selection statements/ conditional statements.
	2) Iterative statements
	3) Transfer Statements
2) The keyword patterns
3) Loop patterns

The conditional or selection statements are are `if`,  `if-else`,`if-elif-else` 


EXAMPLE :--

```python
my_age = int(input("Enter your age"))
if my_age == 32
	print("I am 32 years old")
print("Good Morning!")
```

```python 
num = int(input('enter a number: '))
if num%2 == 0:
	print("Even number")
else:
	print("Odd number")	
```

```
if test expression:
	body of if
elif test expression:
	body of elif
else:
	body of else
```

```python
num1 = 9
num2 = -12
num3 = 7

if num1 <num2 and num1 < num3:
	print(f"1: The smallest number is {num1}")
elif num2 < num3:
	print(f"2: The smallest number is {num2}")
else:
	print(f"3: The smallest number is {num3}")
```

<mark style="background: #ABF7F7A6;">if-elif-else ladder:-</mark>

```python
my_age = float(input(""Enter the age: ))

if my_age > 0 and my_age < 1.5:
	print("The age is of an infant")
	
elif my_age >= 1.5 and my_age < 12:
	print("The age is of child")
	
elif my_age >= 17 and my_age < 30:
	print("The age is of Teenager")
	
elif my_age >= 30 and my_age < 46:
	print("The age is of middle aged person")
	
else:
	print("The age is of a elder person")
``` 


---

Python provides two types of the iterations. One by using for loop, and second by using while loop. There is no concept of `do-while` loop in python. The conditional statement written using for and while loop are generally <mark style="background: #BBFABBA6;">known as iterative statements</mark> because the block of statements written under the body of `for` and `while` loop will be executed 'n' number of times. 

### For loop


The for loop in python iterates in a sequence of elements. The sequence can be either string list, string, tuple, set or range To do some necessary action for every element present in some sequence, the for loop is used. The syntax of for loop is:-

```python
for val in sequence
	Body of for
```

`range(<start_value>,<stop_value>,<increment_value>)

Example:-

```python
for i in range(4):                             #0 to 3
	print(f"I am: {i}")
	
```

To find sum of first 'n' natural number

```python
num = int(input("Enter the number: "))
total = 0
for i in range(1,num+1):
	total += i
print(total)
```



---
### While loop

In a while loop , a block of code is executed as long as the test expression is True and control will come out if the test expression is False.

```python
while <test expression>
	body of while
```

```python
j = 1
while j<=5:
	print("Welcome Python Beginners :)")
	j += 1
```

<mark style="background: #D3BC8D;">Printing a Multiplication table</mark>

```python
n = int(input("n = ?"))
i = 1
while(i<=10):
	print(n,'X',i '=', n*i)
	i = i+1
print("done")
```

```python
#print all odd numbers < 10

i = 1
while i <= 10:
	if i%2==0:   #even
		continue
	print(i, end= "" )
	i = i+1
```

Demonstration of `for` and `while` loop to iterate through a string

```python
my_string = "Zephyrxx0"
print("for loop working")
for i in range(0, len(my_string)):
	print(my_string[i])
print("while loop working")
j=0

while j<len(my_string):
	print(my_string[i])
	j = j+1
```




---

### Transfer Statements

###### Break:-
Use of break in for and while loop

```python
for num in range(1,6)
	if num == 4:
		break

	print(num)
print("break statement executed")

```


```python
num = 0
while num<6:
	if num == 3:
		break
	print(num)
	num +=1

```


###### Continue:-
The continue statement gives the user the flexibility to skip the remaining part of the code for the current iteration only. The syntax of the command is `continue`. 

```python
for num in range(1,6):
	if num == 4:
		continue
	print(num)
print("continue statement executed on num = 4")
```

```python
num = 0
while num <6:
	num += 1
	if num == 3:
		continue
	print(num)
print("continue statement executed on num = 3")
```


###### Pass:-
This is equivalent to wasting the time of processor. It is very close to the delay calculations. When the pass statement is executed , python will do nothing and so it  is a no operation.
Doesn't show error nor result.
Sometimes, the code is not ready or it is in the initial stage and the are rather executed in the latest state, thus the pass statement will be used to construct a body that will do nothing.

```python
num1 = 32
if num > 32:
	pass          #no output of the program.
```

##### In:-

1) Checks whether the value is present in the sequence or not. The sequence includes list, range, set and so on
```python
name = "saurabh"
if 'x' in name:
	print("x is not in name")
else:
	print("x is in name')
```


2) It is used to iterate through a sequence in a for loop

```python
games = ['cricket','football','basketball']
	for i in games:
		print(i)
```



