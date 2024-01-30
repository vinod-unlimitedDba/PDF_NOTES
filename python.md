<details> 
<summary> CHAPTER 1 Get started 
</summary>

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
Python 3.6.0

Python 2.x Version ≤ 2.7

If you have Python 2 installed, and it is your default version

$ python --version
Python 2.7.13

Now write the following code in the prompt:
>>> print("Hello, World")
>>>
>>> Python 3.x Version ≥ 3.0
print('Hello, World')
Python 2.x Version ≥ 2.6

Python 3 print function in Python 2 with the following import statement:
from __future__ import print_function


Launch an interactive Python shell
By executing (running) the python command in your terminal, you are presented with an interactive Python shell.

$ python
Python 2.7.12 (default, Jun 28 2016, 08:46:01)
[GCC 6.1.1 20160602] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print 'Hello, World'
Hello, World

Alternatively, start the interactive prompt and load file with python -i <file.py>.
In command line, run:
$ python -i hello.py
"Hello World"
>>>

There are multiple ways to close the Python shell:
>>> exit() or >>> quit() -- ctrl+D --- ctrl+c

<details> 
<summary> Section 1.2: Creating variables and assigning values
</summary>

# Integer
a = 2 -----> print(a)                        #   Output: 2
b = 9223372036854775807 ----> print(b)       # Output: 9223372036854775807
# Floating point
pi = 3.14  ------>  print(pi)                # Output: 3.14
# String
c = 'A' ----> print(c)                       # Output: A
# String
name = 'John Doe'  --->print(name)          # Output: John Doe
# Boolean
q = True --->  print(q)                     # Output: True
# Empty value or null data type
x = None  ---->print(x)                     # Output: None

0 = x                    => Output: SyntaxError: can't assign to literal

Rules for variable naming:
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
             


</summary>



