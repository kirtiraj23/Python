# Python
Print("Hello World")

It will print the statement inside the print block.

-----------
Hello World

## Handling Exception:---
try:

    text = input('Enter something --> ')
    
except EOFError:

    print('Why did you do an EOF on me?')
    
except KeyboardInterrupt:

    print('You cancelled the operation.')
    
else:

    print('You entered {}'.format(text))
    
 
 # Raising Exception
 
 You can raise exceptions using the raise statement by providing the name of the error/exception and the exception object that is to be thrown.
The error or exception that you can raise should be a class which directly or indirectly must be a derived class of the Exception class.

class ShortInputException(Exception):
    '''A user-defined exception class.'''
    def __init__(self, length, atleast):
    
        Exception.__init__(self)
        
        self.length = length
        
        self.atleast = atleast

try:

    text = input('Enter something --> ')
    
    if len(text) < 3:
    
        raise ShortInputException(len(text), 3)
        
    # Other work can continue as usual here
    
except EOFError:

    print('Why did you do an EOF on me?')
    
except ShortInputException as ex:

    print(('ShortInputException: The input was ' +
           '{0} long, expected at least {1}')
          .format(ex.length, ex.atleast))
else:

    print('No exception was raised.')
    
    
# Finally:---------------
import sys
import time

f = None
try:
    f = open("poem.txt")
    # Our usual file-reading idiom
    while True:
        line = f.readline()
        if len(line) == 0:
            break
        print(line, end='')
        sys.stdout.flush()
        print("Press ctrl+c now")
        # To make sure it runs for a while
        time.sleep(2)
except IOError:
    print("Could not find file poem.txt")
except KeyboardInterrupt:
    print("!! You cancelled the reading from the file.")
finally:
    if f:
        f.close()
    print("(Cleaning up: Closed the file)")
    
    
    
#### When commands are read from a tty, the interpreter is said to be in interactive mode. In this mode it prompts for the next command with the primary prompt, usually three greater-than signs (>>>); for continuation lines it prompts with the secondary prompt, by default three dots (...). 
    
>>> hi_folks = True

>>> if hi_folks:

            ...     print("Good Morning!")

            ...
Good Morning!

# Numbers:-
>>> 2 + 2

4

>>> 50 - 5*6

20

>>> (50 - 5*6) / 4

5.0

>>> 8 / 5  # division always returns a floating point number

1.6


>>> 17 / 3  # classic division returns a float

5.666666666666667

>>>

>>> 17 // 3  # floor division discards the fractional part

5

>>> 17 % 3  # the % operator returns the remainder of the division

2

>>> 5 * 3 + 2  # result * divisor + remainder

17

With Python, it is possible to use the ** operator to calculate powers 1:

>>>

>>> 5 ** 2  # 5 squared

25

>>> 2 ** 7  # 2 to the power of 7

128

>>> width = 20

>>> height = 5 * 9

>>> width * height

900

# Strings

>>> 'spam eggs'  # single quotes

'spam eggs'

>>> 'doesn\'t'  # use \' to escape the single quote...

"doesn't"

>>> "doesn't"  # ...or use double quotes instead

"doesn't"

>>> '"Yes," they said.'

'"Yes," they said.'

>>> "\"Yes,\" they said."

'"Yes," they said.'

>>> '"Isn\'t," they said.'

'"Isn\'t," they said.'

>>> '"Isn\'t," they said.'

'"Isn\'t," they said.'

>>> print('"Isn\'t," they said.')

"Isn't," they said.

>>> s = 'First line.\nSecond line.'  # \n means newline

>>> s  # without print(), \n is included in the output

'First line.\nSecond line.'

>>> print(s)  # with print(), \n produces a new line

First line.

Second line.

>>> print('C:\some\name')  # here \n means newline!

C:\some

ame
>>> print(r'C:\some\name')  # note the r before the quote

C:\some\name

String literals can span multiple lines. One way is using triple-quotes: """...""" or '''...'''. End of lines are automatically included in the string, but it’s possible to prevent this by adding a \ at the end of the line. The following example:

print("""\
Usage: thingy [OPTIONS]
     -h                        Display this usage message
     -H hostname               Hostname to connect to
""")

produces the following output (note that the initial newline is not included):

Usage: thingy [OPTIONS]
     -h                        Display this usage message
     -H hostname               Hostname to connect to
     
Strings can be concatenated (glued together) with the + operator, and repeated with *:

>>>
>>> # 3 times 'un', followed by 'ium'

>>> 3 * 'un' + 'ium'

'unununium'

Two or more string literals (i.e. the ones enclosed between quotes) next to each other are automatically concatenated.

>>>

>>> 'Py' 'thon'

'Python'

This feature is particularly useful when you want to break long strings:

>>>

>>> text = ('Put several strings within parentheses '
...         'to have them joined together.')

>>> text

'Put several strings within parentheses to have them joined together.'

This only works with two literals though, not with variables or expressions:

>>> prefix = 'Py'

>>> prefix 'thon'  # can't concatenate a variable and a string literal

File "<stdin>", line 1
    prefix 'thon'
                ^

SyntaxError: invalid syntax
>>> ('un' * 3) 'ium'
  File "<stdin>", line 1
    ('un' * 3) 'ium'
                   ^
SyntaxError: invalid syntax
    
If you want to concatenate variables or a variable and a literal, use +:

>>>

>>> prefix + 'thon'

'Python'

Strings can be indexed (subscripted), with the first character having index 0. There is no separate character type; a character is simply a string of size one:

>>> word = 'Python'

>>> word[0]  # character in position 0

'P'

>>> word[5]  # character in position 5

'n'

Indices may also be negative numbers, to start counting from the right:


>>>

>>> word[-1]  # last character

'n'

>>> word[-2]  # second-last character

'o'

>>> word[-6]

'P'

In addition to indexing, slicing is also supported. While indexing is used to obtain individual characters, slicing allows you to obtain substring:

>>>

>>> word[0:2]  # characters from position 0 (included) to 2 (excluded)

'Py'

>>> word[2:5]  # characters from position 2 (included) to 5 (excluded)

'tho'



Note how the start is always included, and the end always excluded. This makes sure that s[:i] + s[i:] is always equal to s:

>>>

>>> word[:2] + word[2:]

'Python'

>>> word[:4] + word[4:]

'Python'

Slice indices have useful defaults; an omitted first index defaults to zero, an omitted second index defaults to the size of the string being sliced.

>>>

>>> word[:2]   # character from the beginning to position 2 (excluded)

'Py'

>>> word[4:]   # characters from position 4 (included) to the end

'on'

>>> word[-2:]  # characters from the second-last (included) to the end

'on'

One way to remember how slices work is to think of the indices as pointing between characters, with the left edge of the first character numbered 0. Then the right edge of the last character of a string of n characters has index n, for example:

 +---+---+---+---+---+---+
 | P | y | t | h | o | n |
 +---+---+---+---+---+---+
 0   1   2   3   4   5   6
-6  -5  -4  -3  -2  -1


Attempting to use an index that is too large will result in an error:

>>>

>>> word[42]  # the word only has 6 characters

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>

IndexError: string index out of range

However, out of range slice indexes are handled gracefully when used for slicing:

>>>

>>> word[4:42]

'on'

>>> word[42:]

''

---
Python strings cannot be changed — they are immutable. Therefore, assigning to an indexed position in the string results in an error:

>>>
>>> word[0] = 'J'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
>>> word[2:] = 'py'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
If you need a different string, you should create a new one:

>>>

>>> 'J' + word[1:]

'Jython'

>>> word[:2] + 'py'

'Pypy'

The built-in function len() returns the length of a string:

>>>

>>> s = 'supercalifragilisticexpialidocious'

>>> len(s)

34

# Lists

Python knows a number of compound data types, used to group together other values. The most versatile is the list, which can be written as a list of comma-separated values (items) between square brackets. Lists might contain items of different types, but usually the items all have the same type.

>>>

>>> squares = [1, 4, 9, 16, 25]

>>> squares

[1, 4, 9, 16, 25]

Like strings (and all other built-in sequence types), lists can be indexed and sliced:

>>>

>>> squares[0]  # indexing returns the item

1

>>> squares[-1]

25

>>> squares[-3:]  # slicing returns a new list

[9, 16, 25]

All slice operations return a new list containing the requested elements. This means that the following slice returns a new (shallow) copy of the list:

>>>

>>> squares[:]

[1, 4, 9, 16, 25]

Lists also support operations like concatenation:

>>>

>>> squares + [36, 49, 64, 81, 100]

[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

Unlike strings, which are immutable, lists are a mutable type, i.e. it is possible to change their content:

>>>

>>> cubes = [1, 8, 27, 65, 125]  # something's wrong here

>>> 4 ** 3  # the cube of 4 is 64, not 65!
64

>>> cubes[3] = 64  # replace the wrong value

>>> cubes

[1, 8, 27, 64, 125]

You can also add new items at the end of the list, by using the append() method (we will see more about methods later):

>>>

>>> cubes.append(216)  # add the cube of 6

>>> cubes.append(7 ** 3)  # and the cube of 7

>>> cubes


Assignment to slices is also possible, and this can even change the size of the list or clear it entirely:

>>>

>>> letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']

>>> letters

['a', 'b', 'c', 'd', 'e', 'f', 'g']

>>> # replace some values

>>> letters[2:5] = ['C', 'D', 'E']

>>> letters

['a', 'b', 'C', 'D', 'E', 'f', 'g']

>>> # now remove them

>>> letters[2:5] = []

>>> letters

['a', 'b', 'f', 'g']

>>> # clear the list by replacing all the elements with an empty list

>>> letters[:] = []

>>> letters

[]

The built-in function len() also applies to lists:

>>>

>>> letters = ['a', 'b', 'c', 'd']
>>> len(letters)
4

It is possible to nest lists (create lists containing other lists), for example:

>>>
>>> a = ['a', 'b', 'c']
>>> n = [1, 2, 3]
>>> x = [a, n]
>>> x
[['a', 'b', 'c'], [1, 2, 3]]
>>> x[0]
['a', 'b', 'c']
>>> x[0][1]
'b'
[1, 8, 27, 64, 125, 216, 343]

# if Statements:

Perhaps the most well-known statement type is the if statement. For example:

>>>


>>> x = int(input("Please enter an integer: "))

Please enter an integer: 42

>>> if x < 0:

...     x = 0

...     print('Negative changed to zero')

... elif x == 0:

...     print('Zero')

... elif x == 1:

...     print('Single')

... else:

...     print('More')

...

More


# for Statements

The for statement in Python differs a bit from what you may be used to in C or Pascal. Rather than always iterating over an arithmetic progression of numbers (like in Pascal), or giving the user the ability to define both the iteration step and halting condition (as C), Python’s for statement iterates over the items of any sequence (a list or a string), in the order that they appear in the sequence. For example (no pun intended):

>>>

>>> # Measure some strings:

... words = ['cat', 'window', 'defenestrate']

>>> for w in words:

...     print(w, len(w))

...

cat 3

window 6

defenestrate 12

>>> for w in words[:]:  # Loop over a slice copy of the entire list.

...     if len(w) > 6:

...         words.insert(0, w)

...

>>> words

['defenestrate', 'cat', 'window', 'defenestrate']

# The range() Function
If you do need to iterate over a sequence of numbers, the built-in function range() comes in handy. It generates arithmetic progressions:

>>>

>>> for i in range(5):

...     print(i)

...

0

1

2

3

4

range(5, 10)
   
   5, 6, 7, 8, 9

range(0, 10, 3)
  
  0, 3, 6, 9

range(-10, -100, -30)
 
 -10, -40, -70
 
 >>> a = ['Mary', 'had', 'a', 'little', 'lamb']

>>> for i in range(len(a)):

...     print(i, a[i])

...

0 Mary

1 had

2 a

3 little

4 lamb

A strange thing happens if you just print a range:

>>>

>>> print(range(10))

range(0, 10)

In many ways the object returned by range() behaves as if it is a list, but in fact it isn’t. It is an object which returns the successive items of the desired sequence when you iterate over it, but it doesn’t really make the list, thus saving space.

We say such an object is iterable, that is, suitable as a target for functions and constructs that expect something from which they can obtain successive items until the supply is exhausted. We have seen that the for statement is such an iterator. The function list() is another; it creates lists from iterables:

>>> list(range(5))

[0, 1, 2, 3, 4]


# break and continue Statements, and else Clauses on Loops
The break statement, like in C, breaks out of the innermost enclosing for or while loop.

Loop statements may have an else clause; it is executed when the loop terminates through exhaustion of the list (with for) or when the condition becomes false (with while), but not when the loop is terminated by a break statement. This is exemplified by the following loop, which searches for prime numbers:

>>>

>>> for n in range(2, 10):

...     for x in range(2, n):

...         if n % x == 0:

...             print(n, 'equals', x, '*', n//x)

...             break

...     else:

...         # loop fell through without finding a factor

...         print(n, 'is a prime number')

...

2 is a prime number

3 is a prime number

4 equals 2 * 2

5 is a prime number

6 equals 2 * 3

7 is a prime number

8 equals 2 * 4

9 equals 3 * 3

>>> for num in range(2, 10):

...     if num % 2 == 0:

...         print("Found an even number", num)

...         continue

...     print("Found a number", num)

Found an even number 2

Found a number 3

Found an even number 4

Found a number 5

Found an even number 6

Found a number 7

Found an even number 8

Found a number 9

# pass Statements

The pass statement does nothing. It can be used when a statement is required syntactically but the program requires no action. For example:

>>>

>>> while True:

...     pass  # Busy-wait for keyboard interrupt (Ctrl+C)

...

This is commonly used for creating minimal classes:


>>>

>>> class MyEmptyClass:

...     pass

...

Another place pass can be used is as a place-holder for a function or conditional body when you are working on new code, allowing you to keep 
thinking at a more abstract level. The pass is silently ignored:

>>>

>>> def initlog(*args):

...     pass   # Remember to implement this!

...

# Defining Functions

We can create a function that writes the Fibonacci series to an arbitrary boundary:


>>>

>>> def fib(n):    # write Fibonacci series up to n

...     """Print a Fibonacci series up to n."""

...     a, b = 0, 1

...     while a < n:

...         print(a, end=' ')

...         a, b = b, a+b

...     print()

...

>>> # Now call the function we just defined:

... fib(2000)

0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597

A function definition introduces the function name in the current symbol table. The value of the function name has a type that is recognized by the interpreter as a user-defined function. This value can be assigned to another name which can then also be used as a function. This serves as a general renaming mechanism:


>>>

>>> fib

<function fib at 10042ed0>

>>> f = fib

>>> f(100)

0 1 1 2 3 5 8 13 21 34 55 89

Coming from other languages, you might object that fib is not a function but a procedure since it doesn’t return a value. In fact, even functions without a return statement do return a value, albeit a rather boring one. This value is called None (it’s a built-in name). Writing the value None is normally suppressed by the interpreter if it would be the only value written. You can see it if you really want to using 

print():


>>>

>>> fib(0)

>>> print(fib(0))

None

It is simple to write a function that returns a list of the numbers of the Fibonacci series, instead of printing it:

>>>

>>> def fib2(n):  # return Fibonacci series up to n

...     """Return a list containing the Fibonacci series up to n."""

...     result = []

...     a, b = 0, 1

...     while a < n:

...         result.append(a)    # see below

...         a, b = b, a+b

...     return result

...

>>> f100 = fib2(100)    # call it

>>> f100                # write the result

[0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]

This example, as usual, demonstrates some new Python features:



The return statement returns with a value from a function. return without an expression argument returns None. Falling off the end of a function also returns None.

The statement result.append(a) calls a method of the list object result. A method is a function that ‘belongs’ to an object and is named obj.methodname, where obj is some object (this may be an expression), and methodname is the name of a method that is defined by the object’s type. Different types define different methods. Methods of different types may have the same name without causing ambiguity. (It is possible to define your own object types and methods, using classes, see Classes) The method append() shown in the example is defined for list objects; it adds a new element at the end of the list. In this example it is equivalent to result = result + [a], but more efficient.


The most useful form is to specify a default value for one or more arguments. This creates a function that can be called with fewer arguments than it is defined to allow. For example:

def ask_ok(prompt, retries=4, reminder='Please try again!'):

    while True:

        ok = input(prompt)
        
        if ok in ('y', 'ye', 'yes'):
        
            return True
        
        if ok in ('n', 'no', 'nop', 'nope'):
            
            return False
            
        retries = retries - 1
        
        if retries < 0:
                raise ValueError('invalid user response')
                print(reminder)
                
                
                
The list data type has some more methods. Here are all of the methods of list objects:

list.append(x)

Add an item to the end of the list. Equivalent to a[len(a):] = [x].

list.extend(iterable)

Extend the list by appending all the items from the iterable. Equivalent to a[len(a):] = iterable.

list.insert(i, x)

Insert an item at a given position. The first argument is the index of the element before which to insert, so a.insert(0, x) inserts at the front of the list, and a.insert(len(a), x) is equivalent to a.append(x).

list.remove(x)

Remove the first item from the list whose value is equal to x. It raises a ValueError if there is no such item.

list.pop([i])

Remove the item at the given position in the list, and return it. If no index is specified, a.pop() removes and returns the last item in the list. (The square brackets around the i in the method signature denote that the parameter is optional, not that you should type square brackets at that position. You will see this notation frequently in the Python Library Reference.)

list.clear()

Remove all items from the list. Equivalent to del a[:].


list.index(x[, start[, end]])

Return zero-based index in the list of the first item whose value is equal to x. Raises a ValueError if there is no such item.

The optional arguments start and end are interpreted as in the slice notation and are used to limit the search to a particular subsequence of the list. The returned index is computed relative to the beginning of the full sequence rather than the start argument.

list.count(x)

Return the number of times x appears in the list.

list.sort(key=None, reverse=False)

Sort the items of the list in place (the arguments can be used for sort customization, see sorted() for their explanation).

list.reverse()

Reverse the elements of the list in place.

list.copy()

>>> fruits = ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']

>>> fruits.count('apple')

2

>>> fruits.count('tangerine')

0

>>> fruits.index('banana')
3


>>> fruits.index('banana', 4)  # Find next banana starting a position 4

6

>>> fruits.reverse()

>>> fruits

['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange']

>>> fruits.append('grape')

>>> fruits

['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange', 'grape']

>>> fruits.sort()

>>> fruits

['apple', 'apple', 'banana', 'banana', 'grape', 'kiwi', 'orange', 'pear']

>>> fruits.pop()

'pear'

Return a shallow copy of the list. Equivalent to a[:].

To implement a queue, use collections.deque which was designed to have fast appends and pops from both ends. For example:

>>>

>>> from collections import deque

>>> queue = deque(["Eric", "John", "Michael"])

>>> queue.append("Terry")           # Terry arrives

>>> queue.append("Graham")          # Graham arrives

>>> queue.popleft()                 # The first to arrive now leaves

'Eric'

>>> queue.popleft()                 # The second to arrive now leaves

'John'

>>> queue                           # Remaining queue in order of arrival

deque(['Michael', 'Terry', 'Graham'])

# List Comprehensions

List comprehensions provide a concise way to create lists. Common applications are to make new lists where each element is the result of some operations applied to each member of another sequence or iterable, or to create a subsequence of those elements that satisfy a certain condition.

For example, assume we want to create a list of squares, like:

>>>

>>> squares = []

>>> for x in range(10):

...     squares.append(x**2)

...

>>> squares

[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

or 

squares = list(map(lambda x: x**2, range(10)))

or 

squares = [x**2 for x in range(10)]

istcomp combines the elements of two lists if they are not equal:

>>>

>>> [(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]

[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]

and it's equivalent to 

>>> combs = []

>>> for x in [1,2,3]:

...     for y in [3,1,4]:

...         if x != y:

...             combs.append((x, y))

...

>>> combs

[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]

# The del statement

>>>

>>> a = [-1, 1, 66.25, 333, 333, 1234.5]

>>> del a[0]

>>> a

[1, 66.25, 333, 333, 1234.5]

>>> del a[2:4]

>>> a

[1, 66.25, 1234.5]

>>> del a[:]

>>> a

[]

del can also be used to delete entire variables:

>>>

>>> del a

# Tuples and Sequences

>>> t = 12345, 54321, 'hello!'

>>> t[0]

12345

>>> t

(12345, 54321, 'hello!')

>>> # Tuples may be nested:

... u = t, (1, 2, 3, 4, 5)

>>> u

((12345, 54321, 'hello!'), (1, 2, 3, 4, 5))

>>> # Tuples are immutable:

... t[0] = 88888

Traceback (most recent call last):

File "<stdin>", line 1, in <module>

TypeError: 'tuple' object does not support item assignment

>>> # but they can contain mutable objects:

... v = ([1, 2, 3], [3, 2, 1])

>>> v

([1, 2, 3], [3, 2, 1])

>>> empty = ()

>>> singleton = 'hello',    # <-- note trailing comma

>>> len(empty)

0

>>> len(singleton)

1

>>> singleton

('hello',)

# Sets

>>> basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}

>>> print(basket)                      # show that duplicates have been removed

{'orange', 'banana', 'pear', 'apple'}

>>> 'orange' in basket                 # fast membership testing

True

>>> 'crabgrass' in basket

False

>>> # Demonstrate set operations on unique letters from two words
...

>>> a = set('abracadabra')

>>> b = set('alacazam')

>>> a                                  # unique letters in a

{'a', 'r', 'b', 'c', 'd'}

>>> a - b                              # letters in a but not in b

{'r', 'd', 'b'}

>>> a | b                              # letters in a or b or both

{'a', 'c', 'r', 'd', 'b', 'm', 'z', 'l'}

>>> a & b                              # letters in both a and b

{'a', 'c'}

>>> a ^ b                              # letters in a or b but not both

{'r', 'd', 'b', 'm', 'z', 'l'}

Similarly to list comprehensions, set comprehensions are also supported:

>>>
>>> a = {x for x in 'abracadabra' if x not in 'abc'}
>>> a
{'r', 'd'}

# Dictionaries

>>> tel = {'jack': 4098, 'sape': 4139}

>>> tel['guido'] = 4127

>>> tel

{'jack': 4098, 'sape': 4139, 'guido': 4127}

>>> tel['jack']

4098

>>> del tel['sape']

>>> tel['irv'] = 4127

>>> tel

{'jack': 4098, 'guido': 4127, 'irv': 4127}

>>> list(tel)

['jack', 'guido', 'irv']

>>> sorted(tel)

['guido', 'irv', 'jack']

>>> 'guido' in tel

True

>>> 'jack' not in tel

False

>>> dict([('sape', 4139), ('guido', 4127), ('jack', 4098)])

{'sape': 4139, 'guido': 4127, 'jack': 4098}

dict comprehensions can be used to create dictionaries from arbitrary key and value expressions:

>>>

>>> {x: x**2 for x in (2, 4, 6)}

{2: 4, 4: 16, 6: 36}

>>> dict(sape=4139, guido=4127, jack=4098)

{'sape': 4139, 'guido': 4127, 'jack': 4098}

>>> dict(sape=4139, guido=4127, jack=4098)

{'sape': 4139, 'guido': 4127, 'jack': 4098}

>>> knights = {'gallahad': 'the pure', 'robin': 'the brave'}

>>> for k, v in knights.items():

...     print(k, v)

...

gallahad the pure

robin the brave


# enumerate() function.

>>>

>>> for i, v in enumerate(['tic', 'tac', 'toe']):

...     print(i, v)

...

0 tic

1 tac

2 toe


>>> questions = ['name', 'quest', 'favorite color']

>>> answers = ['lancelot', 'the holy grail', 'blue']

>>> for q, a in zip(questions, answers):

...     print('What is your {0}?  It is {1}.'.format(q, a))

...

What is your name?  It is lancelot.

What is your quest?  It is the holy grail.

What is your favorite color?  It is blue.

>>> for i in reversed(range(1, 10, 2)):

...     print(i)

...

9

7

5

3

1

>>> basket = ['apple', 'orange', 'apple', 'pear', 'orange', 'banana']

>>> for f in sorted(set(basket)):

...     print(f)

...

apple

banana

orange

pear

>>> import math

>>> raw_data = [56.2, float('NaN'), 51.7, 55.3, 52.5, float('NaN'), 47.8]

>>> filtered_data = []

>>> for value in raw_data:

...     if not math.isnan(value):

...         filtered_data.append(value)

...

>>> filtered_data

[56.2, 51.7, 55.3, 52.5, 47.8]

