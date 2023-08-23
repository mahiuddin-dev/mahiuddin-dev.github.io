---
title: "Markdown Syntax"
date: 2023-08-23T23:09:21+05:30
draft: true
github_link: "https://github.com/mahiuddin-dev/"
author: "Mahiuddin"
slug: python312-is-happening
tags:
  - VS Code
description: Let's talk about the new features and upgrades as well as the deprecations in the new Python3.12..


toc: 
---
In this concise overview, we'll delve into Python 3.12 and its exciting new features. Additionally, I'll provide my personal insights on each enhancement or adjustment.

<!--more-->

## Nested F-Strings

Python 3.12 introduces a captivating feature: nested f-string expressions. Let's explore a fresh example to illustrate this.

```
def create_welcome_message(name: str) -> str:
    return f"Welcome, {f"{name}"}!"

visitor_name = "Jennifer"
welcome_message = create_welcome_message(visitor_name)
print(welcome_message)
# Output: Welcome, Jennifer!

```

### Quote Reuse: 
In Python 3.11, attempting to reuse the same quotation marks within an f-string would result in a SyntaxError. This constraint compelled users to resort to different quotation marks (for instance, using double quotes or triple quotes) if the f-string itself utilized single quotes. However, Python 3.12 introduces a new capability that facilitates more flexible usage:

In Python 3.12 and subsequent versions, you are now able to reuse the same quotation marks that enclose the surrounding f-string without encountering a SyntaxError. This advancement allows for constructs like the following:

Before

```
words = ['Python', '3.11']
print(f"This is {': '.join(words)}")
# Output: This is Python: 3.11

```

After

```
words = ['Python', '3.12']
print(f"This is: {": ".join(words)}")
# Output: This is Python: 3.12

```

It's worth noting that there was previously no explicit limitation on the depth of f-string nesting. However, the inability to reuse string quotes within the expression component of f-strings limited the extent to which f-strings could be nested. Even the most complex f-string nesting prior to this change was constrained as follows:

Before

```
print(f"""{f'''{f'{f"{1+1}"}'}'''}""")
# Output: '2'

```

After

```
print(f"{f"{f"{f"{f"{f"{1+1}"}"}"}"}"}")
# Output: '2'

```

## Multiline F-Strings

A remarkable addition in version 3.12 is the ability to create multiline f-strings. In Python 3.11, expressions within f-strings were required to be defined on a single line, even though outside of f-strings, expressions could span multiple lines (such as defining literal lists over multiple lines). This limitation made the f-strings less readable. However, Python 3.12 introduces the ability to define multi-line expressions within f-strings and include comments as well:

```
greeting = f"Hey there {
    name  # User.name
}"
# Output: Hey there Python

```

## Tokenization

Since Python 3.11, the tokenizer module has been built in Python for examining lexical elements and keywords. Now, with the advent of nested and multiline f-strings in 3.12, this module has been reimplemented in C, resulting in nearly a 40% performance boost. This advancement significantly benefits linting and formatting tools that rely on this module.

## Per-Interpreter GIL

Python 3.12 introduces a groundbreaking feature: the Per-Interpreter GIL. This advancement allows us to exert full control over the Global Interpreter Lock's utilization in sub-interpreters. As the official documentation explains, this feature enables Python programs to optimally utilize multiple CPU cores.

## Distutils Deprecated

The ongoing debate between setuptools and distutils within the Python community has culminated in the decision to phase out the distutils standard library. Setuptools, a feature-rich fork of distutils, has gained widespread preference. Consequently, distutils has been deprecated.

Moreover, pip employs setuptools to create distributions. If you create a virtual environment with Python versions up to 3.11 and pip versions up to 22.1, you'll notice setuptools is pre-installed.

```
$ pip list
Package    Version
---------- -------
pip        23.2.1
setuptools 68.0.0    <--
wheel      0.41.1

```

Given setuptools' independence from distutils and pip's reduced reliance on setuptools for versions 22.1 and beyond, freshly installed Python environments no longer include a distribution tool. The setuptools package no longer depends on the virtualenv package either. Thus, even with setuptools installed, you cannot create a virtual environment using commands like:

```
$ python -m venv venv
# ERROR: venv module is not found.

```

The distutils package has become an external third-party package. To access both virtualenv and setuptools functionalities, separate installations are required.

## kwargs Type Hinting

Python 3.12 introduces significant changes to the typing module. Previously, I used typing.Any for type hinting **kwargs in functions and methods. With Python 3.12, type annotations can be more precise using typing.TypedDict.

```
from typing import TypedDict, Unpack

class Movie(TypedDict):
  name: str
  year: int

def foo(**kwargs: Unpack[Movie]): ...

```

## @override Type Hinting

A novel addition in the typing module is the @override type annotation. This annotation helps indicate methods intended for overriding in object-oriented design. This aids typing tools like mypy in identifying code issues.

```
from typing import override

class Parent:
    def greet(self):
        pass

class Child(Parent):
    @override
    def greet(self):
        pass

```

if a typo like changing Child.greet to Child.great occurs, mypy would likely generate non-zero output, indicating the absence of the expected overridden method from the base class.

## New Type Defining

Python 3.12 introduces a new syntax for defining Type Aliases. This new syntax streamlines the process.

Before

```
  from typing import TypeAlias

  Players: TypeAlias = List[str]

  def list_players(players: Players) -> None: ...

```

After

```
type Players = list[str]

def list_players(players: Players) -> None:

```

This convention affects the appearance of functions and methods. For instance, the function scope can be structured as follows:

Before:

```
def analyze_data(data: List[str], values: List[float]) -> None:
```

After:
```
type Data = List[str]
type Values = List[float]

def process_data[data, values](data: Data, values: Values) -> None:
```

The new function definition pattern follows: def NAME[*TYPES](*ARGS: TYPE) -> TYPE. It's important to note that the types preceding the function name are confined to the function's scope.