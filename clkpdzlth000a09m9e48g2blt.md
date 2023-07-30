---
title: "Day 13 Python Basics"
datePublished: Sun Jul 30 2023 11:57:23 GMT+0000 (Coordinated Universal Time)
cuid: clkpdzlth000a09m9e48g2blt
slug: day-13-python-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690717819874/a483ffad-a078-43bb-87b4-5e168e831e46.jpeg
tags: blogging, python, devops, 90daysofdevops, trainwithshubham

---

# **1\. 🐍 What is Python?**

Python, the widely-used programming language, is renowned for its readability, versatility, and simplicity. It was initially created by Guido van Rossum in 1991 and has since grown to become one of the most favored programming languages across the globe.

One of Python’s remarkable features is its support for multiple programming paradigms, including procedural, object-oriented, and functional programming. Being an interpreted language, Python executes code line-by-line during runtime, rather than requiring compilation into machine code beforehand.

In recent times, Python’s popularity has soared, especially in the fields of data science, machine learning, and DevOps. This surge is largely attributed to its powerful libraries, such as NumPy, Pandas, Matplotlib, and Scikit-learn, which have enabled developers to tackle complex data manipulation, visualization, and machine learning tasks efficiently.

# **2\. ⚙️ Installation of Python**

## **2.1 🖥️ Windows**

Follow the below blog to install Python on Windows:

[**Python on Windows**](https://www.digitalocean.com/community/tutorials/install-python-windows-10)

## **2.2 🐧 Linux**

To install Python on Linux, we have to execute the below commands

```plaintext
sudo apt-get update   sudo apt-get install python3
```

To see which version of Python 3 you have installed

```plaintext
python3 --version
```

# **3\. 📚 Variable**

In Python, a variable is a named reference to a value stored in the computer’s memory. It acts as a container for holding data that can be manipulated and accessed within a program. Variables allow you to store various types of data, such as numbers, strings, lists, or even more complex objects.

To create a variable in Python, you simply choose a name and assign a value to it using the assignment operator (=). For example:

```plaintext
message = "Hello Readers"
# Here message is the variable name, and "Hello Readers" is the value assigned to the variable, which is of type String in Python.
```

To print output to the console, you can use the “print()” function to display the contents of a variable or any other desired output:

```plaintext
print(message)
```

When you execute the `print()` function with the variable name `message`, it will display the value assigned to the `message` variable, which, in this case, is “Hello Readers”.

![](https://cdn-images-1.medium.com/max/1000/1*PBsFkstBz6PqktDDh-joLQ.png align="left")

# **4\. 🔢 Data Types in Python**

In Python, data types can be categorized as either mutable or immutable.

![](https://cdn-images-1.medium.com/max/1000/0*gkuIWzl_g9da64vy align="left")

## **4.1 🔄 Mutable Data Type**

A **mutable data type** is one that can be modified after it has been created. Whenever an operation is performed on a mutable object, the object itself is modified.

Examples of mutable data types in Python include:

**Lists:**

A list is an ordered sequence of elements written using square brackets (\[\]). Lists can simultaneously hold different types of data.

Example:

```plaintext
names = ["Harsh", "Mudit", 1, 2, 3]
```

**Sets:**

A set is an unordered collection of unique elements, and duplicate values are not allowed.

Example:

```plaintext
set_1 = {1, 2, 3, 4}
```

**Dictionaries:**

A dictionary is an unordered collection of key-value pairs. It is useful for retrieving data in an optimized way among a large amount of data.

Example:

```plaintext
person = {1: "Harsh", 2: "Rajotya", "age": 23}
```

## **4.2 🔒 Immutable Data Type**

**Immutable Data Type:**

An immutable data type is one whose value cannot be changed after it has been created. Whenever an operation is performed on an immutable object, a new object is created.

Examples of immutable data types in Python include:

Numbers:

* Integer: Represents whole numbers, both positive and negative.
    
* Float: Represents floating-point numbers with decimal points.
    
* Complex: Represents numbers with a real and an imaginary part.
    

Example:

```plaintext
x = 7  # Integer
y = 9.8  # Float
z = 1 + 3j  # Complex
```

**String:**

Strings are sequences of characters represented in single or double quotation marks.

Example:

```plaintext
message = "Hello Viewers"
```

**Tuples:**

Tuples are used to store multiple items in a single variable. They are ordered and unchangeable.

Example:

```plaintext
company = ("TCS", "Accenture", "IBM", "Google", "Microsoft")
```

**Boolean:**

Booleans represent one of two values: True or False.

Example:

```plaintext
a = 8
b = 3
print(a > b)  # True
```