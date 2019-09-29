---
layout: post
title: Chapter 3 Introduction To Programming
date: 2019-08-30 19:00:00 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: TSTP_Chapter3_500.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [The Self-Taught Programmer , Python]
---

Print Hello World a hundred times

{% highlight python %}
for i in range(100):
	print('Hello World')
{% endhighlight %}

***Comment :*** 
: Explains what a line of code does, something that is not obvious. Use comments sparingly not on every line  

***Keywords :*** 
: Words with special meanings within a language

{% highlight python %}
print\
("Testing the \\ to extend code to the next line" )
{% endhighlight %}

***Spacing :*** 
: python requires appropriate spacing because it makes code it easier to read, which is one of its core principals. Other languages use keywords/brackets instead of spacing  

***Data Type :*** 
: data grouped into a specific category

***Object :*** 
: Data value with 3 properties identity, data type and value

***String/str :*** 
: Data type used to represent texts a sequence of one or more characters surrounded by " "

***Integer/int :*** 
: Data type used to represent whole numbers

***Floating Point Numbers/float :*** 
: Data type used to represent decimal numbers 

***Booleans/bool :*** 
: Data type used to represent True or False
    
***NoneType/None :*** 
: Data type used to represent the absence of a value    

{% highlight python %}
a_str   = "Hello World"
a_int   = 1
a_float = 1.1234
a_bool  = False 
a_none  = None 

print(a_str, a_int, a_float, a_bool, a_none)

print(type(a_str), type(a_int), type(a_float), type(a_bool), type(a_none))
{% endhighlight %}

***Constant :*** 
: a value that never changes 

***Variable :*** 
: consists of a name made up of one or more characters, refers to a value that can change  

***Assignment Operator, = :*** 
: used to assign a value to a variable name

Increment/Decrement 
{% highlight python %}
a_int += 10
a_int -= 5
print(a_int)
{% endhighlight %}

Naming variables rules  
* Vars can have spaces, use an underscore _
* vars can only contain letters/numbers/underscores
* Vars can't start with a number, starting with an underscore is reserved for special cases 
* Vars can't use keywords 

***Syntax :*** 
: set of rules/principals/processes that govern the structure of sentences in a given language 

***Syntax Error :*** 
: code written with a disregard to the languages syntax, syntax errors are fatal, the code will not run

***Exception :*** 
: any error that is not a syntax error is considered an exception, not always fatal 


Syntax and Exception error
{% highlight python %}
a_syntaxError = "Hello World"

an_exception = 100/0
{% endhighlight  %}

***Operators :*** 
: symbols used with operands in expressions, grouped into categories

***Arithmetic Operators :*** 
: operators used in arithmetic expressions 

Operator Examples 

{% highlight python %}
a_exponent = 2**2

#Integer division, drops remainder 
a_int_div = 13//2.5

#Module, returns remainder of division (2 goes into 13 x6 times)
a_module = 86 % 3 #13-(2*6) = 1

a_div = 13 / 2.5

{% endhighlight %}

***Operands :*** 
: a value on either side of an operator 

***Expression :*** 
: Two operands and an operator make up an expression

***Order Of Operations :*** 
: set of rules used in mathematical calculations to evaluate an expression (P.E.M.D.A.S)

{% highlight python %}
ex_1 = 2 + 2 * 2 
ex_2 = (2+2) * 2
{% endhighlight %}

***Comparison Operators :*** 
: operators used in expressions, evaluate to True or False

{% highlight python %}
greaterThan      =  10 > 5
lessThan         =  10 < 100
greaterOrEqualTo =  10 >= 10
lessOrEqualTo    =  10 <= 11
equal            =  10 == 10
notEqual         =  10 != 11

print(greaterThan, lessThan, greaterOrEqualTo, lessOrEqualTo, equal, notEqual)
{% endhighlight %}


***Logical Operators :*** 
: operators that evaluate two expressions, return True or False

{% highlight python %}
andOperator = 1 == 1 and 2 == 2 #both
orOperator  = 1 == 1 or 2 == 4  #at least one
notOperator = not 1 == 2

print(andOperator, orOperator, notOperator)
{% endhighlight %}

***Control Structure :*** 
: block of code that makes decisions by analyzing the values of variables 

***Conditional Statements :*** 
: a type of control structure, code that can execute additional code conditionally 

***Pseudo-code :*** 
: Notation resembling code used to illustrate an example

***if-else statement :***   
: A programmatic way to say "if this happens do this otherwise do that"  

	***if-statement :*** 
	: line of code starting with keyword if, followed by an expression, ending with a colon ;  
  	followed by an indentation and one or more lines of code, that execute if the expression is True. 

	***else-statement :*** 
	: line of code starting with keyword else, ending with a colon;
  	followed by an indentation and one or more lines of code that execute if the 'if-statement' expression is False

{% highlight python %}
value = 10
if value == 1:
	print('they are equal')
else:
	print('they are not equal')

value = 18 
if value == 1:
	print('value equals 1')
if value % 2 == 0:
	print('values is even')
if value % 2 != 0:
	print('value is odd')
{% endhighlight %}


Nesting if-statements 
{% highlight python %}
if value > 10:
	if value % 2 == 0:
		print('Values is greater than 10 and even')
{% endhighlight %}

***elif-statements(else if) :***   
* elif-statements can be indefinitely added to if-else statements   
* The if-else statement has to evaluate False in order for the elif-statements to be evaluated, otherwise only the if-else code is executed 
* As soon as one of the elif-statements evaluates to True, its code is executed and no more code executes   
* If the if-else and all elif statements evaluate to False, then the else-statement code is executed

{% highlight python %}
value = 50
if value > 10: 
	print('Value is greater than 10')
elif value > 15:
	print('Value is greater than 15')
elif value > 20:
	print('Value is greater than 20')
elif value > 25:
	print('Value is greater than 25')
else:
	print('Not sure about the value')
{% endhighlight %}

***Statements :***   
: a technical term that describes various parts of a a programming language

***Clause :***   
: Consists of two or more lines of code, a header followed by a suite(s)

***Simple Statements :***   
: one line of code

***Compound Statements: :***   
: multiple lines of code made up of one or more clauses, if/if-else statements

***Header :***   
: Line of code in a clause that contains a keyword, followed by a colon ; and indented code(suites)    
  The header controls the suites

***Suite :***   
: Line of code in a clause controlled by a header 

# CHALLENGES
1. Print three different strings 
2. Write a program that prints a message if a value is less than 10 and another if it it's greater than 10 
3. Write a program that prints a message if a value is less than or equal to 10, another if it's greater than 10 but less than 25 and another if it's greater than 10
4. Create a program that divides 2 variables and returns the remainder
5. Create a program that divides 2 variables and returns the quotient 
6. Write a program with a variable age assigned to an integer, that prints different strings depending on what integer the age is.


{% highlight python %}
#1
print("String one")

print("String two")

print("String three")
{% endhighlight %}

{% highlight python %}
#2
value =35

if value >= 10:
	print('Value is greater than or equal to 10')
else: 
	print('Values is less than 10')
{% endhighlight %}


{% highlight python %}
#3
if value <=10: 
	print('value is less than or equal to 10')
elif value <= 25:
	print('value is greater than 10 but less than 25')
else:
	print('value is greater than 25')
{% endhighlight %}

{% highlight python %}
#4
x = 10 
y = 3
remainder_div = x % y
print(remainder_div)
{% endhighlight %}

{% highlight python %}
#5
quotient_div = x // y
print(quotient_div)

{% endhighlight %}

{% highlight python %}
#6
my_age = 17
drinkAge = my_age - 21

if drinkAge >=0:
	print('you can drink')
else: 
	print('you cant drink yet!')
{% endhighlight %}

