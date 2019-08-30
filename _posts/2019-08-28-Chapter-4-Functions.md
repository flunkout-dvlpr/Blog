---
layout: post
title: Chapter 4 Functions
date: 2019-08-28 24:00:00 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: TSTP_Chapter4_500.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [The Self-Taught Programmer, Python]
---

***Functions :***  
: compound statements that can take input/execute instructions/return an output  
Allow to encapsulate functionality for reuse 

***Convention :*** 
: An agreed way of doing things  

***Calling :***    
: Giving a function the input(parameters) it requires to execute the instructions(code) and return it's output

***Parameter :***  
: An input to a function, a function can have one/multiple/no parameters

***Return :***     
: The value a function outputs when you call it, return statement optional

***Passing :***    
: The action of passing a parameter to a function

`def` :      
: Keyword used in python to define a function, specifying the function name/parameters/instructions/return

***Function naming convention :*** 
: No capital letters, words separated by underscore _

Simple function that adds 5 to X, the parameter passed
{% highlight python %}
def f(x):
	return x + 5 

add_five = f(5)
print(add_five)
{% endhighlight %}


***Built-In-Functions :*** 
: a library of functions built into the programming language 

`len()` :   
: takes object and returns its length

`str()` :    
: takes object and returns new object with a str/string data type  (object passed must be able to convert to type)

`int()` :   
: takes object and returns new object with a int/integer data type (object passed must be able to convert to type)

`float()` :  
: takes object and returns new object with a float data type       (object passed must be able to convert to type)

`input()` :   
: takes a string as parameters, displays string on terminal, stores terminal response provided  as str/string 


{% highlight python %}
todays_date = input("What is todays digit date: ")
todays_date_int = int(todays_date)
print(todays_date_int)

if todays_date_int > 15:
	print("Midway through the month!")
else:
	print("The month is just getting started!")
{% endhighlight %}



***Required Parameters :*** 
: required parameters by defined function 

***Optional Parameters :***
: function parameters that are optional. If parameter not passed, default value is used 

Function using required and optional parameters
{% highlight python %}
def add_some(x, y=5):
	return x + y

print(add_some(3))
print(add_some(3, 2))
{% endhighlight %}

***Scope :*** 
: a variable scope refers to what part of the program can read/write to it

***Global Scope :*** 
: Variable defined outside a function/class

***Global Variable :*** 
: variable that can be read/written to from anywhere in the program 

***Local Scope :*** 
: Variable defined within a function or class
`global` :  

: Keyword required to write to a global variable from within a local scope

Function updating global variable using `global` keyword
{% highlight python %}
x = 100

def f():
	global x 
	x += 100
	print(x)
f()

{% endhighlight %}

***Exception Handling :*** 
: allows to test for error conditions   
"catch" exceptions if they occur and determine how to proceed

***try/catch :*** 
: Keywords used to for exception handling 

**NOTE : Do not use defined variables within try statement in except statement, exception could be raised before variable is defined** 

Try/catch statement to handle zero division error 

{% highlight python %}
n = input("Enter numerator: ")
d = input("Enter denominator: ")
n_int = int(n)
d_int = int(d)

try:
	print(n_int/d_int) 
except ZeroDivisionError:
	print("denominator can't be 0")
{% endhighlight %}

***Docstring :***
: comment at top of function explaining what it does and the dataType each parameter needs to be 

Function using docstring comment

{% highlight python %}
def add_some(a, b):
	"""
	Returns the addition of a and b 
	:param x: int 
	:param y: int
	:return int sum of a and b
	"""
	return a + b

print(add_some(1, 1))
{% endhighlight %}


# CHALLENGES 
1. Write a function that takes a number as an input and returns the number squared
2. Create a function that accepts a string as a parameter and prints it 
3. Write a function that takes three required parameters and two optional parameters 
4. Write a program with two functions  
First function should should take an integer as a parameters and divide it by 2
Second function should should take an integer as a parameters and multiply the result by 4  
Call the first function and store the results as a variable, and pass it as a parameter to the second function 
5. Write a function that converts a string to a float, Use exception handling to to catch the exception that can occur
6. Add docstrings to all the functions created

{% highlight python %}
#1
def square_my_number(x):
	"""
	Returns x squared 
	:param x: int
	:return: x multiplied by 2
	"""
	return x**2

print(square_my_number(5))

{% endhighlight %}

{% highlight python %}
#2
def print_my_string(x):
	"""
	Prints x  
	:param x: string
	"""
	print(x)
{% endhighlight %}

{% highlight python %}
#3
def required_and_optionals(a, b, c, d=0, e=0):
	"""
	Prints the addition of a b c d e 
	:param a: int
	:param b: int
	:param c: int
	:param d: int
	:param e: int
	"""
	total_addition  = a + b + c + d + e
	print(total_addition)

required_and_optionals(2, 4, 8)
{% endhighlight %}


{% highlight python %}
#4
def split_my_int(x):
	"""
	Returns takes x an divides by 2 
	:param x: int
	:return: x divided by 2 
	"""
	return x / 2

def quad_my_int(x):
	"""
	Returns x multiplied by 4
	:param x: int
	"""
	return x * 4

int_split = split_my_int(8)

quad_int = quad_my_int(int_split)

print(quad_int)
{% endhighlight %}

{% highlight python %}
#5 
def my_str_to_float(x):
	"""
	Takes x as and returns it as dataType float
	:param x: str
	:return: string converted to float 
	"""
	try: 
		return float(x)
	except ValueError:
		print("Invalid Input")

my_str_to_float("1")
{% endhighlight %}



