### **ARRAYS**

<mark style="background: #ADCCFFA6;">It is a collection of items of same type stored at continuous memory locations.</mark>

- Basic terminologies of array
    
    
    •**Array Index:** In an array, elements are identified by their indexes. Array index starts from 0.
    •**Array element**: Elements are items stored in an array and can be accessed by their index.
    •**Array Length:** The length of an array is determined by the number of elements it can contain
    

How to declare a 2d array:-

```
 int marks_sem[2][3]={1,2,3,4,5,6}         
                    ={{1,2,3}{4,5,6}}
```

- 2D arrays works in a matrix formation
- Refer with the proper index in order to access any particular element.

**For e.g. :-**

```cpp
printf("%d", marks[1][2]);
```

> Write a program to take input as the size of matrix from the user along with its element and display the matrix
> 

---

### **STRINGS**

- String is a collection of characters in a linear sequence
- It is terminated by a null character.

```cpp
char variable[char_size]
```

```cpp
char name[10]={I.N.D.I,A,\0}(6 characters)
```

#### STRING FUNCTION

- C language supports wide range of functions to manipulate strings.
- All inbuilt string functions are defined under `<string.h>` header file, therefore we must include header file.

`strcpy` this function copies string2 into string1

`strcat` it concatenates string2 at the end of string1s

`strlen` this function returns the length of the string1

`strcmp` this function compares based on the ASCII value

.

```cpp
s1="India"
s2=""
```

> Assignment 8: Write a c program to accept a string from console and to display the following console(without built in function)
1] length of the string
2] total number of characters in the string
3] total number of vowels in the string
4] copy one string into another.
> 

---
### FUNCTIONS








---
### **STRUCTURES**

Structure is a way to group several related variables into one place.
Initialized by `struct`, that creates a Structure.
Each variable in the structure is known as member of the structure.
Unlike an array, a structure can contain different data types.

Syntax of Structure:-

```cpp
struct structureName
{
dataType member1;
dataType member2;
...
};
```

For e.g.:-

```c++
struct stuRec /*derived type struct stuRec is defined. Now you can create variable of this type*/
{
int roll_no;
char name[];
float marks;
char grade;
};
```

When a struct type is declared, no storage or memory is allocated. To allocate memory of a given structure type and work with it, we need to create variables

```c++
struct stuRec 
{ 
/*code*/ 
}; 

int main() 
{
struct sturec student1, student2, s[20];

return 0; 
}

```

or
```c++
struct stuRec 
{
//code
}student1, student2, s[20];
```

In order to access these structure members, we use the `.` operator.

`.` is used between the structure variable name and the structure member name we want to access.

Syntax:- `structure variable.element_name`






