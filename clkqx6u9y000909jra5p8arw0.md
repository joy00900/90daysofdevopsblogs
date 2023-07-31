---
title: "Day 14 Python Data Structure"
datePublished: Mon Jul 31 2023 13:42:39 GMT+0000 (Coordinated Universal Time)
cuid: clkqx6u9y000909jra5p8arw0
slug: day-14-python-data-structure
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690810668190/fbb579ed-6e82-4c38-b3cb-0f5cd552017d.png
tags: python, devops, python-beginner, 90daysofdevops, trainwithshubham

---

# **1\. Data Type 📝**

Data types in Python are fundamental categories that define the characteristics and behavior of data. They inform the compiler or interpreter how a programmer intends to use the data. Python has various built-in data types, including:

**1\. Numeric types:** Integers (whole numbers), Complex (numbers with real and imaginary parts), and Float (decimal numbers).

**2\. Sequence types:** Strings (sequences of characters), Lists (ordered collections), and Tuples (immutable ordered collections).

**3\. Boolean type**: Represents the truth values True and False, used for logical operations.

**4\. Set type:** Unordered collections of unique elements, useful for tasks involving mathematical sets.

**5\. Dictionary type:** Collections of key-value pairs, allowing efficient data retrieval based on keys.

Data types in Python are classes, and variables are instances (objects) of these classes. Understanding data types is crucial for writing efficient and error-free code, as it influences how data can be manipulated and processed in the program.

# **2\. Data Structures 📚**

A data structure is a professional way of storing, organizing, processing, and retrieving data. Data structure organizes the information in a way that is easily understandable by both machines and humans. This makes it easy for users to have access to the data they need.

Python data structure is a systematized arrangement of data that enables us to store and access it efficiently and effectively. The goal of using data structures is to reduce the time and space required to execute operations on the data.

![](https://miro.medium.com/v2/resize:fit:875/0*z-Ftv8YO6rVCHPif align="left")

In Python, the data structure is divided into 2 types, **Primitive and Non-Primitive.**

# **3\. Primitive DS vs Non-primitive DS 🔄**

In Python, primitive data structures are basic data types that are built into the language itself. These include integers, floats, boolean, and characters. They are simple and immutable, meaning their values cannot be changed once assigned.

Non-primitive data structures, on the other hand, are more complex and can hold multiple values or objects. Examples of non-primitive data structures in Python include lists, tuples, dictionaries, and sets. Non-primitive data structures are mutable and offer more flexibility for storing and manipulating data.

## **3.1. Primitive DS 🌀**

![](https://miro.medium.com/v2/resize:fit:804/0*LzkWZXCw_trvC1v4 align="left")

1. **Integer:**
    

Integers represent numeric data — they represent whole numbers from negative infinity to infinity.

```plaintext
integer_1 = 100
integer_2 = 50

# various operations on integers
print(integer_1 * integer_2)  
print(integer_1 + integer_2)  
print(integer_1 - integer_2)  
print(integer_1 / integer_2)  
```

![](https://miro.medium.com/v2/resize:fit:628/1*bhx4RhxrI7ny3wGjpy7exw.jpeg align="left")

**2\. Float**

Floating points are used for rational numbers that usually end with a decimal figure.

```plaintext
float_1 = 9.8
float_2 = 3.14

# various operations on floats
print(float_1 * float_2)  
print(float_1 + float_2)  
print(float_1 - float_2)  
print(float_1 / float_2)  
```

![](https://miro.medium.com/v2/resize:fit:875/1*vdX-wqrc3bX3oy2OG5lzXA.png align="left")

**3\. String**

Strings are used to store data that involves characters (e.g., names or addresses). Strings can be created in Python by enclosing a sequence of characters within a pair of single or double quotes.

```plaintext
print("Hello")
a = """My Name is Harsh Rajotya,
 I'm a DevOps Cloud Engineer,
 with 2+ years of experience."""
print(a)
a = "Hello, World!"
print("2nd character:", a[1])
for x in "Mango":
    print(x)
txt = "Life is too short to argue just say Jay Shree Ram and move on"
print("Jay Shree Ram" in txt)
```

![](https://miro.medium.com/v2/resize:fit:875/1*2qS2nST4HVtorfb8--Ds8Q.png align="left")

**4\. Boolean**

Boolean type only has two types of return values: True and False. These return values are interchangeable with the integers 1 and 0.

```plaintext
has_passed = False
marks = 100
if marks > 60:
    has_passed = True

print(has_passed)
```

![](https://miro.medium.com/v2/resize:fit:875/1*1aJU5eJCQRnGG8eXmdD-iA.jpeg align="left")

## **3.2. Non-Primitive DS 🔀**

![](https://miro.medium.com/v2/resize:fit:875/0*Gqmas7IuAjC5GRQE align="left")

# **4\. Built-in DS vs User Defined DS 🔧**

As the name suggests, these Data Structures are built-in with Python which makes programming easier and helps programmers use them to obtain solutions faster. Some examples of built-in data structures include Lists, Tuple, Dictionary, and Set.

User-defined data structures are created by the programmers based on their specific requirements. These can be implemented using built-in data structures or by creating custom classes. Some examples of user-defined data structures include Stack, Queue, LinkedList, and Tree.

## **4.1. Built-in DS 🛠️**

![](https://miro.medium.com/v2/resize:fit:875/0*ZlHEdfnjhkgbmX8a align="left")

1. **List**
    

Lists are used to store data of different data types sequentially. There are addresses assigned to every element of the list, which is called an Index. The index value starts from 0 and goes on until the last element called the positive index. There is also negative indexing which starts from -1 enabling you to access elements from the last to the first.

```plaintext
my_list = [] # create empty list
print("Empty list creation: ", my_list)

my_list = [1, 2, 3, 'Harsh', 3.132] # creating list with data
print("Creating list: ", my_list)

my_list.append([555, 12]) # add as a single element
print("Appended list: ", my_list)

my_list.extend([234, 'Mudit']) # add as different elements
print("Extending the list: ", my_list)

my_list.insert(1, 'Start') # add element at index 1
print("Inserting an element in a position: ", my_list)

count_occurrence = my_list.count(2)  # count the occurrence in the list
print("Counting the occurrence: ", count_occurrence)

del my_list[5] # delete element at index 5
print("Deleting an element at an index: ", my_list)

my_list.remove('Mudit') # remove element with value
print("Removing an element: ", my_list)

a = my_list.pop(1) # pop element from list
print("Popping an element: ", my_list)

my_list.clear() # empty the list
print("Emptying the list: ", my_list)
```

![](https://miro.medium.com/v2/resize:fit:875/1*W6Ui0abLY_wE7yn-zF76Iw.jpeg align="left")

**2\. Tuple**

Tuples are the same as lists are with the exception that the data once entered into the tuple cannot be changed no matter what. The only exception is when the data inside the tuple is mutable, only then the tuple data can be changed.

```plaintext
my_tuple = (1, 2, 3) #create tuple

my_tuple2 = (1, 2, 3, 'rj') #access elements
for x in my_tuple2:       # Printing all the elements
    print(x)

my_tuple = my_tuple + (4, 5, 6) #add elements
```

![](https://miro.medium.com/v2/resize:fit:875/1*P6uo1Tu-_6_KKY2MMbPwmw.jpeg align="left")

**3\. Dictionary**

A dictionary can be created by placing a sequence of elements within curly {} braces, separated by ‘comma’. The dictionary holds pairs of values, one being the Key and the other corresponding pair element being its Key: value. Values in a dictionary can be of any data type and can be duplicated, whereas keys can’t be repeated and must be immutable.

```plaintext
x = {'Harsh': 7, 'Mudit': 10}

x['Harsh'] = 3  # updating the value
print(x)  # All the key-value in the dictionary

print(x['Harsh'])  # get the value of a key

del x['Mudit']  # delete a key
print(x)

x['Deepak'] = 9  # Adding a key value pair
print(list(x))  # Listing all the keys
print(sorted(x))  # Sorting the keys

'Harsh' in x  # Checking if the key is available in the dictionary
'Paul' not in x  # Checking if the key is not there
```

![](https://miro.medium.com/v2/resize:fit:875/1*CVa2gXr5IKXEF7JJQ8IWOg.jpeg align="left")

**4\. Set**

Sets are a collection of unordered elements that are unique. Meaning that even if the data is repeated more than one time, it would be entered into the set only once. It resembles the sets that you have learned in arithmetic. The operations also are the same as are with the arithmetic sets.

```plaintext
# Create a set with duplicate elements
my_set = {1, 2, 3, 4, 5, 5, 5}

# Add element 4 to the set
my_set.add(4)

# Check if 5 is in the set
print(5 in my_set)  # Output: True

# Print the set (duplicates have been removed)
print(my_set)  # Output: {1, 2, 3, 4, 5}

# Create sets from strings
a = set('abracadabra')
b = set('alacazam')

# Print the unique letters in sets a and b
print(a)  # Output: {'a', 'r', 'b', 'c', 'd'}
print(b)  # Output: {'a', 'l', 'c', 'z', 'm'}

# Set operations
print(a - b)  # Output: {'d', 'b', 'r'} (letters in a but not in b)
print(a | b)  # Output: {'a', 'c', 'b', 'l', 'd', 'z', 'r', 'm'} (letters in a or b or both)
print(a & b)  # Output: {'a', 'c'} (letters in both a and b)
print(a ^ b)  # Output: {'b', 'l', 'd', 'z', 'r', 'm'} (letters in a or b but not both)
```

![](https://miro.medium.com/v2/resize:fit:875/1*Hj2Ib0ye5agRushsSRPtFA.jpeg align="left")

## **4.2. User-Defined DS 🧰**

![](https://miro.medium.com/v2/resize:fit:875/0*Wr37muZjH7hxGtxc align="left")

**Linear DS**

1. **Array**
    

Arrays in Python are Data Structures that can hold multiple values of the same type. Often, they are misinterpreted as lists or Numpy Arrays. Technically, Arrays in Python are distinct from both these.

```plaintext
cars = ["Ford", "Volvo", "BMW", "Volvo"]

print(cars[2])  # Accessing the element at index 2
print(len(cars))  # Getting the length of the list

for x in cars:  # Iterating and printing all elements in the list
    print(x)

cars.append("Honda")  # Adding one more element to the list
print(cars)

cars.count("Volvo")  # Counting the number of occurrences of "Volvo" in the list
print(cars)

cars.pop(1)  # Deleting the second element from the list
print(cars)

cars.remove("BMW")  # Deleting the element that has the value "BMW"
print(cars)

cars.clear()  # Removing all the elements from the list
print(cars)
```

![](https://miro.medium.com/v2/resize:fit:875/1*Vl-iqTHTxQsONMxhAE6snw.png align="left")

**2\. Stack**

Stacks are linear Data Structures that are based on the principle of Last-In-First-Out (LIFO) where data that is entered last will be the first to get accessed.

It is built using the array structure and has operations namely, pushing (adding) elements, popping (deleting) elements and accessing elements only from one point in the stack called the TOP. This TOP is the pointer to the current position of the stack.

Stacks are prominently used in applications such as Recursive Programming, reversing words, undo mechanisms in word editors and so forth.

![](https://miro.medium.com/v2/resize:fit:875/0*8oKVXPcE5YiwVyok align="left")

**3\. Queue**

A queue is also a linear data structure that is based on the principle of First-In-First-Out (FIFO) where the data entered first will be accessed first.

It is built using the array structure and has operations that can be performed from both ends of the Queue, that is, head-tail or front-back. Operations such as adding and deleting elements are called En-Queue and De-Queue and accessing the elements can be performed.

Queues are used as Network Buffers for traffic congestion management, used in Operating Systems for Job Scheduling and many more.

![](https://miro.medium.com/v2/resize:fit:875/0*T2tmrkJUOsf3sTo9 align="left")

**4\. LinkedList**

Linked lists are linear Data Structures that are not stored consequently but are linked with each other using pointers. The node of a linked list is composed of data and a pointer called next. These structures are most widely used in image-viewing applications, music player applications and so forth.

![](https://miro.medium.com/v2/resize:fit:875/0*Xk18bgEhAW7tfkVr align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*d0lDKe2wO3uYCusn align="left")

**Non-Linear DS**

1. **Tree**
    

Trees are non-linear Data Structures that have roots and nodes. The root is the node from where the data originates and the nodes are the other data points that are available to us. The node that precedes is the parent and the node after is called the child.

There are levels a tree has to show the depth of information. The last nodes are called the leaves. Trees create a hierarchy that can be used in a lot of real-world applications such as the HTML pages use trees to distinguish which tag comes under which block. It is also efficient for searching purposes and much more.

![](https://miro.medium.com/v2/resize:fit:875/0*oyjbN1SHO0_jrKD8 align="left")

**2.Graph**

Graphs are used to store data collection of points called vertices (nodes) and edges (edges).

Graphs can be called the most accurate representation of a real-world map. They are used to find the various cost-to-distance between the various data points called the nodes and hence find the least path.

Many applications such as Google Maps, Uber, and many more use Graphs to find the least distance and increase profits in the best ways.

![](https://miro.medium.com/v2/resize:fit:875/0*7KPkVbTyfzxUntsB align="left")

# **5\. Task ✅**

1.Give the Difference between List, Tuple and Set. Do Handson and put screenshots as per your understanding.

List: A list is Mutable, which is an ordered collection of items. And the items in the list can be replaced or changed.

Set: A set is Mutable, which is an unordered collection of items. And the items can not be changed or replaced.

Tuple: A Tuple is immutable, which is an ordered collection of items. And the items cannot be changed or replaced.

```plaintext
# List
l = ["Harsh", "Mudit", 7, 211.3, 5 + 11j]
print(l)           # Print the list
print(type(l))     # Print the type of the variable 'l'

# Set
s = {1, 2, 4, 2, 7, 5, 9, 7, 8, 9}
print(s)           # Print the set
print(type(s))     # Print the type of the variable 's'

# Tuple
t = (1, "Harsh", 24.3)
print(t)           # Print the tuple
print(type(t))     # Print the type of the variable 't'
```

![](https://miro.medium.com/v2/resize:fit:875/1*UjzMtdjZglecejlHAuoyCw.jpeg align="left")

2\. Create the below Dictionary and use Dictionary methods to print your favorite tool just by using the keys of the Dictionary.

```plaintext
fav_tools = { 
   1: "Linux", 
   2: "Git", 
   3: "Docker", 
   4: "Kubernetes", 
   5: "Terraform", 
   6: "Ansible", 
   7: "Chef"
}

print(" Fav tools are: ",fav_tools)
print("My fav tool:",fav_tools[3])
```

![](https://miro.medium.com/v2/resize:fit:875/1*8OkpVPa0kp9kbXSCISBVJA.png align="left")

3\. Create a List of cloud service providers eg.

```plaintext
cloud_providers = ["AWS", "GCP", "Azure"]
print(cloud_providers)
```

![](https://miro.medium.com/v2/resize:fit:875/1*uSuHHU6KXpmMX8kfg1HdgA.png align="left")

4\. Write a program to add Digital Ocean to the list of cloud\_providers and sort the list in alphabetical order.

```plaintext
cloud_providers = ["AWS", "GCP", "Azure"]
print(cloud_providers)

# Adding a new cloud provider to the list
cloud_providers.append("Digital Ocean")
print(cloud_providers)

# Printing the list in sorted order
print(sorted(cloud_providers))
```

![](https://miro.medium.com/v2/resize:fit:875/1*fvcXkvs4t2sQmwaJM1WAXA.png align="left")