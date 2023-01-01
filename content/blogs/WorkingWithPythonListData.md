---
title: "Working With Python List Data"
date: 2022-10-06T15:49:22+06:00
draft: true
github_link: "https://github.com/mahiuddin-dev/"
author: "Mahiuddin"
# image: /images/blogs/
tags:
  - Python
  - List
description: ""
toc: 
---

Working With Python List Data. Data is everywhere. Programming is all about data, processing data, acquiring data, understanding data.
<!--more-->

## Data
All Programs process data and Python are no exception. To work with data effectivaly we need somewhere put our data when processing it. In Python everything is an object. That's mean number, string, modules, function everything. And any object can be assigned to a variable. But there's really not a lot more to storing single data values in variables. Lets look at Python built-in support for storing a collection of values.

## Four Built In Data Structures in Python
Python comes with four built-in data structures that we can use to hold any collection of objects and they are <b>List</b>, <b>Tuple</b>, <b>Set</b> and <b>Dictionary</b>. All four of these data structures are always available Python code and they do not need to be imported to use.

## Ordered / Unordered
List and Tuple are a ordered collection.If specific order is not important to use. Python comes with two Unordered data structures. these are Set and Dictionary. List and Dictionary are Mutable, Tuple is Immutable. So now big question is What is Mutable and Immutable?

## Mutable
Python List is an example of a mutable data structure, in that it can change at runtime. We cadan grow and shrink a list b adding and removing objects as needed. It's also possible to change any object stored in any slot. 

## Immutable
This means that once we assign objects to a (Tuple). The Tuple can not be changed under any circumstance. It is often useful to think of a Tuple as a constant list.

## Working With List
If you know any programming language you should heard about array. In python a list is like an array, in that we can think of a list as being an indexed collection of releted objects, with each slot in the list numbered from 0. In python list is dynamic. There are no need to predeclare the size of a list. List is also heterogeneous that means no need to predeclare the type of the objects where storing. We can store any kind of data in list. few secends ago we knew thta list is also mutable. 

Before learning how to work with lists, let's spend some time learning how to spot lists in Python code.

## Spot a list in Code
In Python List are always enclosed in <b>square brackets</b>, and the object contained within the list are always separeted by a <b>comma</b>. When a list created where the objects are assigned to a new list directly in code. Python refer to this as a literal list, in that the list is created and populated in one go.

## Creating Lists Literally
Our First example Create a Empty List called <b>numbers</b>. And then assignig some data on this list.
``` 
numbers = []  
numbers = [2,4,6,8]  
```
Let's create another list called <b>city</b>
```
city = ['Dinajpur', 'Rangpur', 'Dhaka']
```
Let's create another List where we store strings, float and integer in this example are all Python objects, so they can be stored in a list if needed.
```
laptop_details = ['HP', 'Ubuntu', 20.4, 2022]
```
We can put everything in a new list like:
```
everything = [numbers, city, laptop_details]
```
And this everything list output is like:
```
everything = [ [2,4,6,8], ['Dinajpur', 'Rangpur', 'Dhaka'], ['HP', 'Ubuntu', 20.4, 2022] ]
```
