
[Ques 14]([CodeTantra Edu](https://sitnagpur.codetantra.com/secure/topic-details1.jsp?cid=6580418d3d5f37412ee31a35&tid=658041cb3d5f37412ee31a75&bd=AMTc1Nl9jdF9jaA==))
```python
a= int(input("Enter first number: "))
b= int(input("Enter second number: "))
c= int(input("Enter third number: "))
d = []

d.append(a)
d.append(b)
d.append(c)
#Check if the entered digits are valid (between 0-9)

if 0<=a <=9 and 0<=b <=9 and 0<=c <=9:
	for i in range(0,3):                    #Generate all possible combinations
		for j in range(0,3):
			for k in range(0,3):
				if(i != j & j !=k & k!=i):
					print(d[i],d[j],d[k])
else:
	print("Invalid")
```

```python
a= int(input("digit1 (0-9): "))
b= int(input("digit2 (0-9): "))
c= int(input("digit3 (0-9): "))

#Check if the entered digits are valid (between 0-9)
if 0<=a <=9 and 0<=b <=9 and 0<=c <=9:          #Generate all possible combinations
	combinations = [100 * a + 10 * b + c, 100 * a + 10 * c + b, 100 * b + 10 * a + c, 100 * b + 10 * c + a, 100 * c + 10 * a + b, 100 * c + 10 * b + a,]

	for combination in combinations:
		print(combination)
else:
	print("Invalid)
```

```python
a= int(input("digit1 (0-9): "))
b= int(input("digit2 (0-9): "))
c= int(input("digit3 (0-9): "))

#Check if the entered digits are valid (between 0-9)
if 0<=a <=9 and 0<=b <=9 and 0<=c <=9:
	#Generate all possible combinations
	print("%d%d%d", %(a,b,c))
	print("%d%d%d", %(a,c,b))
	print("%d%d%d", %(b,a,c))
	print("%d%d%d", %(b,c,a))
	print("%d%d%d", %(c,a,b))
	print("%d%d%d", %(c,b,a))

else:
	print("Invalid")
```

---

Ques) Write a Python program to check prime number.

```python
num = int(input("Enter a number: "))

if num > 1:
	for i in range(2, num):
		if (num % i) == 0:
			print(num,"is not a prime number")
			break
		else:
			print(num,"is a prime number")
else:
	print(num,"is not a prime number")
```

---

Ques) Write a Python program that prints prime numbers less than n which represents the upper limit.

```python
#range function does not count last number, its always in the form of (n-1)
#only 1 -100 is counted

for i in range(2,n):
	for j in range(2,n):
		if i % j == 0:
			break
		if i == j:
			print(i)          #print(i, end=" ")
```

---
Ques) Write a Python program that prints prime numbers from lower limit to upper limit.

```python
l_range = int(input("Enter lower range: "))
u_range = int(input("Enter upper range: "))

print("Prime numbers between",l_range "and" u_range "are:- ")

#all prime number are greater than 1
if num > 1:
	for i in range(2, num):
		if (num % i == 0):
			break
		else:
			print(num)
```

---

Ques) Write a program to count the number of vowels using sets in a given string.

```python
string = str(input("enter: "))
vowels = "aeiouAEIOU"

count = sum(string.count(vowel) for vowel in vowels)

print(count)
```

```python
string = str(input("Enter string: "))
count = 0
vowels = set("aeiouAEIOU")
for letter in string:
	if letter in vowels:
		count =+ 1
print("Count of the vowels is:", count)
```

---
