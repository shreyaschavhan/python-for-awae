```
I'm preparing for OSCP, so the repo name makes sense! ;) plus, it's my personal notes. 
It's good if you find it helpful, if not I don't care. Thanks!
```

## ⁍ 𝐏𝐲𝐭𝐡𝐨𝐧 𝐅𝐨𝐫 𝐄𝐭𝐡𝐢𝐜𝐚𝐥 𝐇𝐚𝐜𝐤𝐞𝐫𝐬 : 𝐅𝐫𝐨𝐦 𝐛𝐞𝐠𝐢𝐧𝐧𝐞𝐫𝐬 𝐭𝐨 𝐀𝐝𝐯𝐚𝐧𝐜𝐞𝐝 

- `29th March 2022` - Started
- `12th April 2022` - Expected
- Expected Footnotes:
  - `Learn Python 3 The Hard Way`
  - `Learn More Python 3 The Hard Way`
  - `Violent Python`
  - `Black Hat Python`
  - [The Complete Python Hacking Course: Beginner To Advance! (2021)](https://youtu.be/0NQ2aMxBYNE)
  - [The Complete Python Hacking Course Playlist](https://youtube.com/playlist?list=PL9bcYdRTwTIme7BckMbAd55KdwEzeSe9m)


## ‣ 𝐓𝐚𝐛𝐥𝐞 𝐨𝐟 𝐂𝐨𝐧𝐭𝐞𝐧𝐭𝐬

- [Basics](#𝐁𝐚𝐬𝐢𝐜𝐬)
	- Printing anything
	- Adding Comments
	- Numbers and Maths
	- Variables
	- Escape
	- Taking Input
	- Read File
	- Reading and writing files
	- Copying one file to another
	- Functions
	- If-elif-else
	- For loop
	- while loop
	- Old Style String Format
	- Operators
	- Dictionary
	- Class/Object in python
- [Violent Python](#𝐕𝐢𝐨𝐥𝐞𝐧𝐭-𝐏𝐲𝐭𝐡𝐨𝐧)
	- [Installing a library](#-𝐈𝐧𝐬𝐭𝐚𝐥𝐥𝐢𝐧𝐠-𝐚-𝐥𝐢𝐛𝐫𝐚𝐫𝐲) 

## 𝐁𝐚𝐬𝐢𝐜𝐬

- Printing anything

```
print("Hello there!")
print("Repo Name: Python for OSCP")
```

- Adding Comments : 
  - `using # (called as hash or pound or octothorpe (lol, funny name!))`

```
# This is a single line comment

"""
This
is a
multiline 
Comment
"""
```

- Numbers and Maths
  
```
+: plus
-: minus
/: slash
*: asterisk
%: percent
<: less-than
>: greater-than
<=: less-than-equal
>=: greater-than-equal
```

- Variables

```
name = "Shreyas"

print("My name is ", name)
print(f"What man!? You have ear problems. Listen again! MY NAME IS {name}. GOT IT?")
print("I'm pissed now. Here is my name: {}".format(name))
```

- use `\n` to end line
- use `\t` for tab
- escape quotes

```
print("I'm 6'1\" ft tall")
print('I\'m 6\'1" ft tall')
```

- Escape

Escape | What it does
--- | ---
`\\` | Backslash (\)
`\'` | Single Quote (')
`\"` | Double Quote (")
`\a` | ASCII bell (BEL)
`\b` | ASCII backspace (BS)
`\f` | ASCII formfeed (FF)
`\n` | ASCII linefeed (LF)
`\N{name}` | Character named name in the Unicode database (Unicode only)
`\r` | Carriage return (CR)
`\t` | Horizontal tab (TAB)
`\uxxxx` | Character with 16-bit hex value xxxx
`\Uxxxxxxxx` | Character with 32-bit hex value xxxxxxxx
`\v` | ASCII vertical tab (VT)
`\ooo` | Character with octal value ooo
`\xhh` | Character with hex value hh

- Taking input

```
age = input("How old are you? ")
```

- Taking arguments as input on terminal

```
from sys import argv

script, first, second, third = argv

print("The script is called: ", script)
print("First Variable is: ", first)
print("Second Variable is: ", second)
print("Third Variable is: ", third)
```
```
$ python arguments.py first 2nd 3rd
The script is called: arguments.py
First variable is: first
Second variable is: 2nd
Third variable is: 3rd
```

- Read file

```
from sys import argv

script, filename = argv

txt = open(filename)
print(txt.read())
```

- Reading and writing files
```
- `close` : Closes the file. Like `File -> Save`... in your editor
- `read`: Reads the contents of the file. You can assign the result to a variable
- `readline`: Reads just one line of a text file.
- `truncate`: Empties the file. Watch out if you care about the file.
- `write('stuff')`: Writes "stuff" to the file.
- `seek(0)`: Move the read/write location to the beginning of the file.
```

```
from sys import argv

script, filename = argv

print("Opening the file...")
target = open(filename, 'w')

print("Truncating the file. Goodbye!")
target.truncate()

print("Let's write a line.")
target.write("Hey! My name is shreyas")

target.close()
```

- copying one file to another

```
from sys import argv

script, from_file, to_file = argv
file1 = open(from_file)
data = file1.read()

file2 = open(to_file, 'w')
file2.write(data)

file2.close()
file1.close()
```

- Functions

```
# this one is like your scripts with argv
def print_two(*args):
	arg1, arg2 = args
	print(f"arg1: {arg1}, arg2: {arg2}")

# ok, that *args is actually pointless, we can just do this
def print_two_again(arg1, arg2):
	print(f"arg1: {arg1}, arg2: {arg2}")

print_two("Shreyas", "Chavhan")
print_two_again("Shreyas", "Chavhan")

```

- if, elif, else

```
if test expression:
    Body of if
elif test expression:
    Body of elif
else: 
    Body of else
```

- list

```
a = [1, 2, 3, 4, 5]
# this is a list

print(a[1]) # prints element at index 1
```

- for loop

```
a = [1, 2, 3, 4, 5]
for i in a:
  print(i)
```

- while loop

```
i = 0;
while i < 6:
  print(i)
  i += 1
```

- Old style String Format

Escape | Description
--- | ---
`%d` | Decimal integers (not floating point)
`%i` | Same as %d
`%o` | Octal number
`%u` | Unsigned decimal
`%x` | Hexadecimal lowercase
`%X` | Hexadecimal uppercase
`%e` | Exponential notation, lowercase "e"
`%E` | Exponential notation, uppercase "E"
`%f` | floating point real number
`%F` | Same as %f
`%g` | Either %f or %e, whichever is shorter
`%G` | Same as %g but uppercase
`%c` | character format
`%r` | Repr format (debugging format)
`%s` | String format
`%%` | A percent sign

- Operators

Operator | Description 
---|---
`+` | Addition
`-` | Subtraction
`*` | Multiplication
`**` | Power of
`/` | Division
`//` | Floor Division
`%` | String interpolate or modulus
`<` | Less than
`>` | Greater than
`<=` | Less than equal
`>=` | Greater than equal
`==` | Equal
`!=` | Not equal
`( )` | Parentheses
`[ ]` | List brackets
`{ }` | Dict curly braces
`@` | At (decorators)
`,` | Comma
`:` | Colon
`.` | Dot
`=` | Assign Equal
`;` | Semi-colon
`+=` | Add and assign
`-=` | Subtract and assign
`*=` | Multiply and assign
`/=` | Divide and assign
`//=` | Floor divide and assign
`%=` | Modulus assign
`**=` | Power assign

- Dictionary

```
>>> stuff = {'name': 'Zed', 'age': 39, 'height': 6 * 12 + 2}
>>> print(stuff['name'])
Zed
>>> print(stuff['age'])
39
```

- Class/Object in python

```
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

p1 = Person("John", 36)

print(p1.name)
print(p1.age)
```

## 𝐕𝐢𝐨𝐥𝐞𝐧𝐭 𝐏𝐲𝐭𝐡𝐨𝐧

##### • 𝐈𝐧𝐬𝐭𝐚𝐥𝐥𝐢𝐧𝐠 𝐚 𝐥𝐢𝐛𝐫𝐚𝐫𝐲

```
$ pip install python-nmap
Collecting python-nmap
  Downloading python-nmap-0.7.1.tar.gz (44 kB)
     ---------------------------------------- 44.4/44.4 KB 1.1 MB/s eta 0:00:00
  Preparing metadata (setup.py) ... done
Using legacy 'setup.py install' for python-nmap, since package 'wheel' is not installed.
Installing collected packages: python-nmap
  Running setup.py install for python-nmap ... done
Successfully installed python-nmap-0.7.1

```

## 𝐌𝐨𝐝𝐮𝐥𝐞𝐬
