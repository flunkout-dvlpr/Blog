---
layout: post
title: Chapter 5 Containers
date: 2019-08-29 19:30:00 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: TSTP_Chapter5_500.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [The Self-Taught Programmer, Python]
---

***Methods :***
: Functions closely associated to a given type of data  
A method is called on an object

{% highlight python %}
print("hello".upper())
print("hello".replace("l", "1"))
{% endhighlight %}

***List :*** 
: A container that stores objects in a specific order   
Represented by brackets   
Can store any data type, is mutable

There a two syntaxes to create a list 

{% highlight python %}
fruit = list()
fruit = []
fruit = ["orange", "banana", "mango"]
{% endhighlight %}

`append()` :
: Method used to add items to a list  
Always adds to end of list 

{% highlight python %}
fruit.append("strawberry")

print(fruit)
{% endhighlight %}


***Iterable :*** 
: An object is iterable when you can access each item using a loop   
Each item has an index   
A number representing it's position  

***Iterables :*** 
: Objects that can be iterated, string/list/tuples  

**NOTE : first item in a list always has an index of 0**  
Retrieve item with its index 

`print(fruit[0])`

***IndexError :*** 
: Exception raised when when index accessed doesn't exist 

***Mutable :***
: Container that can have items added or removed 

***Immutable :***
: Container that contents cannot be changed  (the characters in a string)

`pop()` : 
: Method used to remove last element in a list 

{% highlight python %}
fruit[0] = "watermelon"
print(fruit[0])

fruit.pop()
print(fruit)
{% endhighlight %}

Combine lists using addition operator

{% highlight python %}
list1 = ['a', 'b', 'c']
list2 = ['e', 'f', 'g']

print(list1 + list2)
{% endhighlight %}  

*Check if an item exists in a list using logical operator 'in'*  
*Check if an item not in a list using logical operator 'not in'*  

{% highlight python %}
print('a' in list1)
print('a' not in list2)
{% endhighlight %}

Get number of items in list using `len()` method  

{% highlight python %}
print(len(list1))
{% endhighlight %}

***Tuple :***
: A container that stores objects in a specific order  
Represented with parentheses   
Is immutable(contents can't change)  

There a two syntaxes to create a tuple 

{% highlight python %}
colors = tuple()
colors = ()
colors = ("orange", "blue", "red")
{% endhighlight %}

**NOTE : Even if a tuple only has one item a comma is required after it** 

{% highlight python %}
one_item_tuple = ("one item",)
print(type(one_item_tuple))
{% endhighlight %}

Retrieve item with its index 

{% highlight python %}
print(colors[0])
{% endhighlight %}

*Check if an item exists in a tuple using logical operator 'in'*  
*Check if an item not in a tuple using logical operator 'not in'*

{% highlight python %}
print('blue' in colors)
print('pink' not in colors)
{% endhighlight %}

**NOTE: tuples are useful when dealing with values that will never change**

***Dictionaries :***
: Container for storing objects, used to link one object(Key) to another object(Value).   
Resulting in a key-value pair  
Are mutable  
Not stored in specific order    
Represented with curly brackets   

***Mapping :***
: Linking one object to another

***key-value pair :***
: `{key : value}`

**NOTE : keys can be looked-up in dictionaries to get value, but values cannot be used to lookup keys**  
There a two syntaxes to create a dict

{% highlight python %}
my_dict = dict()
my_dict = {}

fruit_colors = {'banana' : 'yellow',
		'strawberry' : 'red',
		'grape' : 'purple' }
{% endhighlight %}

Add values to dict with `dictName[Key] = value`

{% highlight python %}
fruit_colors['pear'] = 'green'
{% endhighlight %}

**NOTE: any object can be a dict Value, but a dict Key must be immutable**  
*Check if a Key exists in a dict using logical operator 'in'     (cannot be used to check for a Value)*  
*Check if a Key is not in a dict using logical operator 'not in' (cannot be used to check for a Value)*


`del` :
: keyword used to delete a key-value pair form a dict

{% highlight python %}
print(fruit_colors)

del fruit_colors['banana']

print(fruit_colors)
{% endhighlight %}

Store lists in other lists 

{% highlight python %}
lists = []

fruits = ["pear", "banana", "mango"]
colors = ['green', 'yellow', 'yellow-orange'] 
shapes = ['square', 'circle', 'triangle']

lists.append(fruits)
lists.append(colors)
lists.append(shapes)
print(lists)
{% endhighlight %}

Appending an item to one of the original lists will also update the list containing all lists
{% highlight python %}
furits = lists[0]
furits.append("watermelon")

print(furits)

print(lists)
{% endhighlight %}

Store tuples in lists 

{% highlight python %}
locations = []

la = (34.22, 188.24)
chicago = (41.81, 87.62)

locations.append(la)
locations.append(chicago)

print(locations)
{% endhighlight %}

# CHALLENGES

1. Create a list of your favorite musicians 
2. Create a list of tuples, with each tuple containing the longitude and latitude of somewhere you've visited.
3. Create a dictionary that contains different attributes about you
4. Write a program that lets the user ask your attributes and returns the result from the dictionary you created
5. Create a dictionary mapping your favorite musicians to a list of your favorite songs by them

 
{% highlight python %}
#1
my_favorite_rappers = ["Kendrick Lamar", "Drake", "Meek Mill"]
{% endhighlight %}


{% highlight python %}
#2
palces_visited = [ (29.7604, 95.3698), (30.2672, 97.7431), (32.7767, 96.7970)]
{% endhighlight %}


{% highlight python %}
#3
my_attributes = {'name': 'Julio',
				 'age': 23,
				 'gender': 'male'}
{% endhighlight %}


{% highlight python %}
#4
answer = input("Enter which attribute to display: name, age or gender ")

if answer in my_attributes:
    result = my_attributes[answer]
    print(result)
{% endhighlight %}


{% highlight python %}
#5
my_favorite_songs = {'Kendrick': ['I', 'Good Kid Mad City'],
					'J.Cole': ['Djavu', 'Young Simba'],
					'Drake': ['Too Much', '305 In My City']}
{% endhighlight %}
