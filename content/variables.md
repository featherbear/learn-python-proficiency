---
title: "Variables"
layout: "bundle"
outputs: ["Reveal"]
date: 2020-09-18T00:40:38+10:00
---

{{< slide class="center" >}}

## Variables

---

## Variables

A variable contains data which can be accessed and and modified in the program

A variable has a `data type` - which specifies the nature of the data - i.e whether the variable is a number, a picture, a word...

> `myVariable = 'hello'`  

> `myOtherVariable = 185.2`

---

## Language Semantics

{{% fragment %}}
In Python, variables are **strongly typed** - variable types must agree with the operation

```
10 + 10     # Will work
'10' + '10' # Will work
'10' + 10   # Will cause an error
```
{{% /fragment %}}

{{% fragment %}}
In Python, variables are **dynamically typed** - meaning that the type of a variable can vary during runtime

```python
a = 'hello' # `a` is a string
a = 10      # `a` is now an integer
```
{{% /fragment %}}

---

## Types

Python has many inbuilt types

* `int`
* `float`
* `str`
* `list`
* `str`
* `bool`
* etc ...

Custom data types can also be created by implementing [classes](../classes)

---

## Converting Between Types

Several inbuilt functions exist to convert a data type into another data type

```python
var = "15"
int(var)      # 15
str(int(var)) # "15"
```

---

## Deleting Variables

To delete a variable, the following syntax can be used

> `del >>variableName<<`

```python
name = 'Jason'
print(name)
del name
```

Deleting variables helps to reduce memory usage, but is often not required

---

## Function Variables

The scope of a variable refers to the regions of the program which can access a variable.

If a function defines a variable (by assignment) that _shadows_ a variable in the outer scope (i.e. same name), the outer-scoped variable will be inaccessible

---

## Function Variables

{{% section %}}

If a function defines a variable (by assignment) that _shadows_ a variable in the outer scope (i.e. same name), the outer-scoped variable will be inaccessible

```python
a = 5

def doSomething():
    a = 6      # a is 6 only in the function
    print(a)

doSomething()  # 6
print(a)       # 5 - a is still 5
```

---

To affect the outer scope variable, the `global` keyword is needed

```python
a = 5

def doSomething():
    global a   # global scope specifier
    a = 6
    print(a)

doSomething()  # 6
print(a)       # 6 - a is now 6
```

---

Nested functions must redeclare any variable scope specifiers, else they will create their own local function variables.

```python
a = 1

def doTheThing():
    a = 2
    def doTheOtherThing():
        a = 3
        return a
    print("doTheOtherThing", doTheOtherThing()) # 3
    return a

print("doTheThing", doTheThing())               # 2
print("toplevel", a)                            # 1
```

---

For a nested function, the `nonlocal` scope specifier is used instead of `global`

```python
a = 1

def doTheThing():
    a = 2
    def doTheOtherThing():
        nonlocal a       # nonlocal scope specifier
        a = 3
        return a
    print("doTheOtherThing", doTheOtherThing()) # 3
    return a

print("doTheThing", doTheThing())               # 3
print("toplevel", a)                            # 1
```

---

If a `global` specifier is used in a subfunction, it will reference the top-level variable, bypassing the outer-function variable

```python
a = 1

def doTheThing():
    a = 2
    def doTheOtherThing():
        global a
        a = 3
        return a
    print("doTheOtherThing", doTheOtherThing()) # 3
    return a

print("doTheThing", doTheThing())               # 3
print("toplevel", a)                            # 3
```

---

### TL;DR

* Use the `global` keyword in a function that uses an outer-scope variable
* Use the `nonlocal` keyword in a subfunction that uses an outer-function variable
* A scope specifier is only required if a shadowed variable is modified by assignment.

{{% /section %}}

---

## Variable dictionary access

```python
myGlobalVar = 5

def doIt():
  globals()['myGlobalVar'] = 10

  myLocalVar = 20
  locals()['myLocalVar'] = 50

  print("myLocalVar", myLocalVar) # 20 - not changed!
  
doIt()
print("myGlobalVar", myGlobalVar) # 10 - changed!
```

{{% section %}}

In Python, variables are stored in special dictionaries that are accessible through the `locals()` and `globals()` function.

---

Using `globals()` is a solution to global variable shadowing problems, as the dictionary reflects the actual global values

---

**NOTE**: The `globals()` dictionary will update the global variables, however the `locals()` dictionary does not guarantee the reflection of values 

{{% /section %}}