---
title: "Day 15 Python Libraries"
datePublished: Thu Aug 10 2023 05:55:45 GMT+0000 (Coordinated Universal Time)
cuid: cll4qwwlb000g0al7e5455eyc
slug: day-15-python-libraries
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691646865088/0849e21f-f78a-4400-8bb3-68d85515fb38.jpeg
tags: python, python3, devops, 90daysofdevops, trainwithshubham

---

Python is a versatile programming language with an extensive collection of libraries that make it easier to develop various applications, from web development to data analysis, and more. In this blog post, we will introduce some popular Python libraries that can be useful for different types of projects.

There are some third-party libraries like NumPy, Pandas, matplotlib, Scikit-learn, Flask, Django, etc.

To know more about Python Data Types and Data Structures, I have written a blog: [https://medium.com/@harshBlogs/day-14-python-data-structure-15fa18f4dce7](https://medium.com/@harshBlogs/day-14-python-data-structure-15fa18f4dce7).

# **1\. Python In-Built Libraries**

Python has a wide range of built-in libraries that provide developers with a variety of functionalities to help solve complex programming problems. Some of them are os, sys, datetime, re, math, random, json, yaml, etc.

A good DevOps engineer should know which library needs to be used for a particular action. Because as a DevOps Engineer, you should be able to parse files, be it Txt, json, yaml, etc.

# **2\. JSON File**

JSON stands for “JavaScript Object Notation”, but it’s not limited to just JavaScript and can be used in many programming languages. A JSON file is a file format used for storing and exchanging data.

JSON files are composed of key-value pairs, where the keys are strings and the values can be strings, numbers, arrays, objects, booleans, or null.

*Usage:* JSON is often used to transfer data between web applications and servers as it is lightweight, easy to read and write, and can be parsed by most programming languages.

*Extension:* .json

*Example of a JSON file:*

```plaintext
{
  "name": "XYZ",
  "age": 100,
  "email": "abcde@gmail.com",
}
```

# **3\. YAML File**

YAML stands for “YAML Ain’t Markup Language” which uses indentation to represent data hierarchies and is designed to be easy to read and write by humans.

Like JSON, YAML is a key-value-based format, but it has a more relaxed syntax and can handle more complex data structures, including lists and nested objects.

*Usage:* YAML file is used for configuration files and data exchange between different programming languages.

*Extension:* .yaml or .yml

*Example of a YAML File:*

```plaintext
name: XYZ
age: 100
email: abcde@gmail.com
```

# **4\. Tasks**

## **4.1 Task 1: Create a Dictionary in Python and write it to a JSON File.**

Create a Dictionary named “person” and import the json library.

```plaintext
person = {
    "name": "XYZ",
    "age": 100,
    "email": "abcde@gmail.com",
    "address": {
        "street": "1",
        "city": "pqrst",
        "state": "uvw",
        "zip": "0123456"
    },
    "interests": ["DevOps", "Cricket", "Bikes"]
}
import json
```

![](https://miro.medium.com/v2/resize:fit:875/1*LORWvwuGdyYU2N2nos5MyQ.jpeg align="left")

```plaintext
with open('person.json','w') as f:
    json.dump(person,f)
```

![](https://miro.medium.com/v2/resize:fit:790/1*NEsRl7srbyM75wDrsMj9aQ.jpeg align="left")

`json.dump()` is a function provided by the built-in json module in Python that is used to write a Python object to a JSON file.

After running this code, a new file named “person.json” will be created in the same directory as the Python script, containing the contents of the person dictionary in JSON format.

![](https://miro.medium.com/v2/resize:fit:875/1*fzwSpVZ8rw1EdnhG6-eTig.jpeg align="left")

## **4.2 Task 2: Read a JSON file services.json kept in the Day 15 Task of 90 Days of DevOps Github repo and print the service names of every cloud service provider.**

First, we import the JSON module. Then we read the data into the services.json file.

We then use json.loads()to parse the JSON string and convert it to a Python object called data. We can then access the value of the “services” key by calling data\[“services”\] and storing it in the variable list.

The code for the above task is:

![](https://miro.medium.com/v2/resize:fit:875/1*CK0wJtAyz8U-B-nKnAnxmQ.jpeg align="left")

![](https://miro.medium.com/v2/resize:fit:875/1*ufyeVC8pKeVAKK7_1U2r6w.jpeg align="left")

## **4.3 Task 3: Read the YAML file using Python, file services.yaml, and read the contents to convert YAML to JSON.**

The YAML file is opened using the open() function and load its contents using the [yaml.safe](http://yaml.safe)\_load() function. The json.dumps() function is used to convert the YAML data to a JSON string, which is then printed on the console.

```plaintext
import json
import yaml

yaml_file = "services.yaml"

try:
    with open(yaml_file, "r") as F:
        yaml_contents = yaml.safe_load(F)
        json_contents = json.dumps(yaml_contents, indent=4)  # Convert YAML to JSON with indentation
        print(json_contents)
except FileNotFoundError:
    print(f"File '{yaml_file}' not found.")
```

![](https://miro.medium.com/v2/resize:fit:875/1*ywU8gc578h43O1WhNn0J0A.jpeg align="left")

Well, this was it for this blog. Until then, keep reading my blogs and connect with me on LinkedIn and let’s have a conversation.

To help me improve my blog and correct my mistakes, I am available on LinkedIn as [https://www.linkedin.com/in/harsh-rajotya/](https://www.linkedin.com/in/harsh-rajotya/) . Do reach me and I am open to suggestions and corrections.

#Day15 #90DaysofDevops