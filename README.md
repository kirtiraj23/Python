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
