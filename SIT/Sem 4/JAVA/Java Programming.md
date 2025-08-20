
# *Data Structures*:

- BigDecimal : Java provides a class called [BigDecimal](http://docs.oracle.com/javase/7/docs/api/java/math/BigDecimal.html) for representing and computing decimal numbers with any required precision.  
  
	BigDecimal is not a wrapper class of any primitive data type. It is a convenience class for handling large decimal numbers with arbitrary precision. The value to be represented by BigDecimal should be passed to one of the BigDecimal [constructors](http://docs.oracle.com/javase/1.5.0/docs/api/java/math/BigDecimal.html#constructor_summary).

```Java
MathContext mathContext = new MathContext(5)
BigDecimal x = new BigDecimal("3.14", mathcontext)
```

```Java
x.add(augend,mathContext);
```

- MathContext(n): returns a number with `n` number of digits (including before and after decimal)

> Precision is the total number of digits in a number.

- Character 

	Character.isUpperCase()
	Character.isLowerCase()
	Character.toUpperCase()
	Character.toLowerCase()
	Character.isLetterOrDigit()
	Character.isWhitespace()


# Methods:
- `public` is the access modifier, meaning it determines who can use this method. All of our methods in this chapter will be public
- `static` allows us to call the method without the need of an object
- `return` tells the program what to output when it computes

Method overloading : in same class
Method overriding : In inheritance



