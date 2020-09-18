---
title: "Strings"
layout: "bundle"
outputs: ["Reveal"]
date: 2020-09-18T00:40:45+10:00
---

{{< slide class="center" >}}

## Strings

---

{{< slide class="center" >}}

## Strings

"Hello, World!"

A string is an array of characters.  

{{% fragment %}}
&nbsp;  
&nbsp;  
We can assign a string to a variable

> `my_string = "Hello, World"`
{{% /fragment %}}

---

## Strings

A string is often identified by being surrounded by single or double quotation marks

```python
string1 = 'this is a string'
string2 = "this is also a string"
```

## Quotation Characters

A single quote enclosed string must have its contained single quotes escaped with the `\` character. The same applies for double quoted strings with double quotes.

```python
string3 = 'Good example, isn\'t it?'
string4 = "Wow, programming must be \"so fun\"..."
```

---

## String Functions

There are many inbuilt string functions

* `len(<str>)`
* `<str>.lower()`
* `<str>.upper()`
* `<str>.startswith(...)`
* `<str>.endswith(...)`
* `<str>.zfill(...)`
* ... many more!

---

## Concatenation

Strings can be combined together.

```python
"Hello, " + "World!" # Hello, World!
```

{{% fragment %}}

String variables can also be combined

```python
string5 = "Hello, "
string6 = "World!"

string5 + string6 # Hello, World!
```

{{% /fragment %}}

{{% fragment %}}
String variables can also be added to strings

```python
string5 + "World!" # Hello, World!
```

{{% /fragment %}}

---

## Concatening Non-Strings

Strings can only be concatenated with **other** strings!  
To combine variables and values that are not strings, we must call the `str(...)` method (or similar) on those variables

```python
age = 9
name = "Tony"

name + "is " + age + " years old" # < TypeError >
name + "is " + str(age) + " years old" # Tony is 9 years old

```

---

## List Indexing

In Python, we count from `0`!  
Therefore indexing also starts from zero

```python
string = "ABCDE"
string[0] = "A"
string[1] = "B"
string[2] = "C"
string[3] = "D"
string[4] = "E"

string[5] DOES NOT EXIST
```

---

## List Ranges

```python
string = "ABCDE"
```

{{% section %}}

We can extract part of the string using these indexes

> `stringVariable[from:to-1]`

```python
string[2:4] == "CD"
string[0:3] == "ABC"
```

---

If extracting from the start to a certain index, we can omit the `0`

> `stringVariable[:to-1]`

```python
string[:3] == "ABC"
```

---

If extracting a certain index to the end of the string, we can omit the value after the `:` character

> `stringVariable[3:]`

```python
string[3:] == "DE"
```

{{% /section %}}

---

## List Stepping

We can select a pattern of characters in the string by setting the `step` option of our index.

> `string[from:to-1:step]`

```python
string = "ABCDEF"

string[0:5]   == 'ABCDE'
string[0:5:1] == 'ABCDE'
string[0:5:2] == 'ACE'
string[0:5:3] == 'AD'
```

A negative step could even reverse a string!

```python
string[::-1] == 'EDCBA'
```

---

## Mutability

Whilst we can access a specific position in a string, we cannot directly modify it

```python
myString = "abcde"
myString[2] == "c"
myString[2] = "C" # ERROR
```

---

## String Formatting (1)

String concatenation can be performed through string replacement methods

```python
myFmtString1 = "Hello, %s!" % "world"
```

> `%s` is replaced with a passed string

{{% fragment %}}

If multiple format strings are used, the passed values should be passed as a `tuple`

```python
myFmtString2 = "%s is %d years old" % ("Tony", 9)
```

> `%d` is replaced with a passed integer

{{% /fragment %}}

{{% fragment %}}

`%-format` strings can also use [format modifiers](https://python-reference.readthedocs.io/en/latest/docs/str/formatting.html)

{{% /fragment %}}

---

## String Formatting (2)

Strings also have a `.format(...)` function, which replace the placeholders in a string with values passed into the function.

```python
myFmtString3 = '{1} is {0} years old'.format(9, "Tony")

# Tony is 9 years old. His favourite colour is blue
```

The `.format(...)` function takes in both positional and keyword values

```python
myFmtString4 = "{} goes {sound}".format("cow", sound="moo")

# Cows go moo
```

---

## String Formatting (3)

### F-Strings

Introduced in Python 3.6, format string literals can also be used to format values.

```python
name = "Tony"
age = "9"

f"{name} is {age} years old"
# Tony is 9 years

f"16 x 9 is {16 * 9}"
# 16 x 9 is 144
```

---

## Escape Characters

Escape characters (control data) can be placed in a string, commonly new-line (`\n`) and tab (`\t`) characters

```python
myString1 = "Hello World"
myString2 = "Hello\nWorld"

print(myString1)
# Hello World

print(myString2)
# Hello
# World
```

---

### Multi-line Strings

A string can span multiple lines of code

```python
multilineString1 = """Hello there
this is a
multiline string
"""
```

They function as normal strings, and can be used with string formatting techniques, as well as as an f-string

```python
adjective = "cool"
multilineString2 = f'''
I think
that's pretty {adjective}!
'''
```

---

## Raw Strings

Raw strings prevent escape characters from being evaluated

```python
normalString = "Hello\nWorld!"
# Hello
# World!

rawString = r"Hello\nWorld!"
# Hello\nWorld!
```

---

## Unicode Strings

In Python 2, to use unicode (UTF-8) characters, an encoding header must be put at the start of the file, and the strings needs a `u` prepended to the string

```
-*- coding: utf-8 -*-
# Python 2.X
unicodeString = u"♥"
```

In Python 3, strings are unicode by default, so nothing needs to be done

```python
# Python 3.X
unicodeString = "♥"
```

---

## Byte Strings

Bytes have a numerical value from `0x00` (`0`) to `0xFF` (`255`). A byte-string contains only byte characters.

`<str>.encode()` is used to convert a string into a bytestring
```python
unicodeString = "♥"
unicodeString.encode() # b'\xe2\x99\xa5'
```

`<bytes>.decode()` is used to convert a bytestring into a string

```python
byteString = b'\xf0\x9f\x98\x8a'
byteString.decode() # 😊
```
