<details> 
<summary> CHAPTER 1 Get started </summary>

===>  Python is a widely used high-level programming language for general-purpose programming, created by Guido van
Rossum and first released in 1991.

====> Python features a dynamic type system and automatic memory management
and supports multiple programming paradigms, including object-oriented, imperative, functional programming,
and procedural styles. It has a large and comprehensive standard library.

Two major versions of Python are currently in active use:
Python 3.x is the current version and is under active development.
Python 2.x is the legacy version and will receive only security updates until 2020. No new features will be implemented. 

If you have Python 3 installed, and it is your default version

$ python --version
 >Python 3.6.0
Python 2.x Version ≤ 2.7

If you have Python 2 installed, and it is your default version

$ python --version
> Python 2.7.13

Now write the following code in the prompt:
>>> print("Hello, World")
>>> Python 3.x Version ≥ 3.0
>>>print('Hello, World')
>>>Python 2.x Version ≥ 2.6

Python 3 print function in Python 2 with the following import statement:
from __future__ import print_function

Launch an interactive Python shell
By executing (running) the python command in your terminal, you are presented with an interactive Python shell.

 $python\
     `#Python 2.7.12 (default, Jun 28 2016, 08:46:01)\
    [GCC 6.1.1 20160602] on linux Type "help", "copyright", "credits" or "license" for more information.'
    
     print 'Hello, World'
     >Hello, World

Alternatively, start the interactive prompt and load file with python -i <file.py>.
In command line, run:
$ python -i hello.py
"Hello World"
>>>

There are multiple ways to close the Python shell:
>>> exit() or >>> quit() -- ctrl+D --- ctrl+c

<details> 
<summary> ##Section 1.2: Creating variables and assigning values 
</summary>


### Integer
    a = 2 -----> print(a)                        #   Output: 2\
    b = 9223372036854775807 ----> print(b)       # Output: 9223372036854775807
### Floating point
    pi = 3.14  ------>  print(pi)                # Output: 3.14
### String
    c = 'A' ----> print(c)                       # Output: A
### String
    name = 'John Doe'  --->print(name)          # Output: John Doe
### Boolean
    q = True --->  print(q)                     # Output: True
### Empty value or null data type
    x = None  ---->print(x)                     # Output: None

    0 = x                    => Output: SyntaxError: can't assign to literal

Rules for variable naming:\
    
     1. Variables names must start with a letter or an underscore.
             x = True # valid
            _y = True # valid
            9x = False # starts with numeral        => SyntaxError: invalid syntax
            $y = False # starts with symbol         => SyntaxError: invalid syntax
    
     2. The remainder of your variable name may consist of letters, numbers and underscores.
             has_0_in_it = "Still Valid"

     3. Names are case sensitive.
                x = 9
                y = X*5  =====>    NameError: name 'X' is not defined 
                
Even though there's no need to specify a data type when declaring a variable in Python, while allocating the necessary area in memory for the variable, 
the Python interpreter automatically picks the most suitable built-in type for it:

                a = 2                  ======> print(type(a))            # Output: <type 'int'>
                b = 9223372036854775807 ===> print(type(b))              # Output: <type 'int'>
                pi = 3.14                ====>print(type(pi))            # Output: <type 'float'>
                c = 'A'                 ====> print(type(c))             # Output: <type 'str'>
                name = 'John Doe'        =====> print(type(name))        # Output: <type 'str'>
                q = True                 ====>print(type(q))             # Output: <type 'bool'>
                x = None                ====> print(type(x))             # Output: <type 'NoneType'>

                
You can assign multiple values to multiple variables in one line. Note that there must be the same number of
arguments on the right and left sides of the = operator:

            a, b, c = 1, 2, 3 ======> print(a, b, c)       # Output: 1 2 3
            a, b, c = 1, 2 ====> Traceback (most recent call last): => File "name.py", line N, in <module>
            => a, b, c = 1, 2 ===> ValueError: need more than 2 values to unpack
            a, b = 1, 2, 3 ====> Traceback (most recent call last): => File "name.py", line N, in <module>
            => a, b = 1, 2, 3 ===> ValueError: too many values to unpack


The error in last example can be obviated by assigning remaining values to equal number of arbitrary variables.
This dummy variable can have any name, but it is conventional to use the underscore (_) for assigning unwanted values:
   
    >a, b, _ = 1, 2, 3 ===>print(a, b)     # Output: 1, 2

Note that the number of _ and number of remaining values must be equal. Otherwise 'too many values to unpack
error' is thrown as above:
   
    a, b, _ = 1,2,3,4 ===>Traceback (most recent call last): ===>File "name.py", line N, in <module>
    a, b, _ = 1,2,3,4  ===>ValueError: too many values to unpack (expected 3)           

sometime we can assign several variables simultaneously with single value

            a = b = c = 1 ====> print(a, b, c) # Output: 1 1 1
            a = b = c = 1 # all three names a, b and c refer to same int object with value 1
            print(a, b, c) # Output: 1 1 1
                b = 2 # b now refers to another int object, one with a value of 2
            print(a, b, c)   # Output: 1 2 1 # so output is as expected.

The above is also true for mutable types (like list, dict, etc.) just as it is true for immutable types (like int, string,
tuple, etc.):

        x = y = [7, 8, 9] # x and y refer to the same list object just created, [7, 8, 9]
        x = [13, 8, 9] # x now refers to a different list object just created, [13, 8, 9]
        print(y) # y still refers to the list it was first assigned
        # Output: [7, 8, 9]

Things are a bit different when it comes to modifying the object (in contrast to assigning the name to
a different object, which we did above) when the cascading assignment is used for mutable types.

        x = y = [7, 8, 9] # x and y are two different names for the same list object just created, [7,8, 9]
        x[0] = 13 # we are updating the value of the list [7, 8, 9] through one of its names, x in this case
        print(y) # printing the value of the list using its other name
         # Output: [13, 8, 9] # hence, naturally the change is reflected

Nested lists are also valid in python. This means that a list can contain another list as an element.

        x = [1, 2, [3, 4, 5], 6, 7] # this is nested list
        print x[2] # Output: [3, 4, 5]
        print x[2][1] # Output: 4

Lastly, variables in Python do not have to stay the same type as which they were first defined -- you can simply use
= to assign a new value to a variable, even if that value is of a different type.

        a = 2 print(a) # Output: 2
        a = "New value" print(a) # Output: New value


<details> 
<summary> Section 1.3: Block Indentation  </summary>

===>Python uses indentation to define control and loop constructs. This contributes to Python's readability, however, it
    requires the programmer to pay close attention to the use of whitespace.

Python uses the colon symbol (:) and indentation for showing where blocks of code begin and end (If you come
from another language, do not confuse this with somehow being related to the ternary operator).

blocks in Python, such as functions, loops, if clauses and other constructs, have no ending identifiers.

For example:

        def my_function(): # This is a function definition. Note the colon (:)
        a = 2 # This line belongs to the function because it's indented
        return a # This line also belongs to the same function
        print(my_function()) # This line is OUTSIDE the function block

        or
        if a > b: # If block starts here
        print(a) # This is part of the if block
        else: # else must be at the same level as if
        print(b) # This line is part of the else block

Blocks that contain exactly one single-line statement may be put on the same line, though this form is generally not
considered good style:
        if a > b: print(a)
        else: print(b)
Attempting to do this with more than a single statement will not work:
        if x > y: y = x
        print(y) # IndentationError: unexpected indent
        if x > y: while y != z: y -= 1 # SyntaxError: invalid syntax

An empty block causes an IndentationError. Use pass (a command that does nothing) when you have a block with content:
    def will_be_implemented_later():
    pass

Spaces vs. Tabs
-----------

In short: always use 4 spaces for indentation.

Python 3.x Version ≥ 3.0

Python 3 disallows mixing the use of tabs and spaces for indentation. In such case a compile-time error is
generated: Inconsistent use of tabs and spaces in indentation and the program will not run.

Python 2.x Version ≤ 2.7

<details> 
<summary> Section 1.4: Datatypes </summary>

### Booleans
    1. bool: A boolean value of either True or False. Logical operations like and, or, not can be performed on booleans.
            x or y # if x is False then y otherwise x
            x and y # if x is False then x otherwise y
            not x # if x is True then False, otherwise True

    In Python 2.x and in Python 3.x, a boolean is also an int. The bool type is a subclass of the int type and True and
    False are its only instances:
            issubclass(bool, int) # True
            isinstance(True, bool) # True
            isinstance(False, bool) # True
            
### Numbers
    1. int: Integer number
            a = 2
            b = 100
            c = 123456789
            d = 38563846326424324
    2. float: Floating point number; precision depends on the implementation and system architecture, for
             CPython the float datatype corresponds to a C double.
                    a = 2.0
                    b = 100.e0
                    c = 123456789.e1
    3.complex: Complex numbers
                    a = 2 + 1j
                    b = 100 + 10j
    4.Sequences and collections    

                 Python differentiates between ordered sequences and unordered collections (such as set and dict).
                 strings (str, bytes, unicode) are sequences
                 reversed: A reversed order of str with reversed function
                        a = reversed('hello')

     5.tuple: An ordered collection of n values of any type (n >= 0).
                a = (1, 2, 3)
                b = ('a', 1, 'python', (1, 2))
                b[2] = 'something else' # returns a TypeError    
      
            Supports indexing; immutable; hashable if all its members are hashable

     6.list: An ordered collection of n values (n >= 0)
            
            a = [1, 2, 3]
            b = ['a', 1, 'python', (1, 2), [1, 2]]
            b[2] = 'something else' # allowed
      
      Not hashable; mutable.      
    
    7.set: An unordered collection of unique values. Items must be hashable.
            a = {1, 2, 'a'}            

    8. dict: An unordered collection of unique key-value pairs; keys must be hashable.
                a = {1: 'one',
                     2: 'two'}
                b = {'a': [1, 2, 3],
                     'b': 'a string'}

>An object is hashable if it has a hash value which never changes during its lifetime (it needs a __hash__()
>method), and can be compared to other objects (it needs an __eq__() method).
                     

<details> 
<summary> Section 1.4: Datatypes </summary>

<details> 
<summary> Section 1.4: Datatypes </summary>

<details> 
<summary> Section 1.4: Datatypes </summary>

<details> 
<summary> Section 1.4: Datatypes </summary>




</summary>



