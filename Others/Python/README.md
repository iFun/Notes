## Python Study Notes ##

### Trick
If you want to remove leading and ending spaces, use str.strip():

sentence = ' hello  apple'
sentence.strip()
> 'hello  apple'
If you want to remove all spaces, use str.replace():

sentence = ' hello  apple'
sentence.replace(" ", "")
> 'helloapple'
If you want to remove duplicated spaces, use str.split():

sentence = ' hello  apple'
" ".join(sentence.split())
> 'hello apple'


### String ###

Double quote same as single quote
with triple quotes I can use double or single quote in the string



Strings Are **Immutable**

This means that once you have created a string, you cannot change it. Although this might seem like a bad thing, it really isn't. We will see why this is not a limitation in the various programs that we see later on.


- String builder = format method 
- number are optional

```python

age = 20
name = 'Swaroop'

print('{0} was {1} years old when he wrote this book'.format(name, age))
print('Why is {0} playing with that python?'.format(name))

```


output

python str_format.py

Swaroop was 20 years old when he wrote this book

Why is Swaroop playing with that python?

###string concatenation:
name + ' is ' + str(age) + ' years old'

same but ugly not good practice 



Regex use raw string
use **r** at the front

Always use raw strings when dealing with regular expressions. Otherwise, a lot of backwhacking may be required. For example, backreferences can be referred to as '\\1' or r'\1'.

## Loop##

### Else in while loop###

```python

while running:
    guess = int(input('Enter an integer : '))

    if guess == number:
        print('Congratulations, you guessed it.')
        # this causes the while loop to stop
        running = False
    elif guess < number:
        print('No, it is a little higher than that.')
    else:
        print('No, it is a little lower than that.')
else:
    print('The while loop is over.')
    # Do anything else you want to do here

print('Done')

```
##For loop###
in C/C++, if you want to write for (int i = 0; i < 5; i++), then in Python you write just for i in range(0,5)

##Function##
###Default argument values###
```python
def say(message, times=1):
    print(message * times)

say('Hello')
say('World', 5)

```
###Keyword arguments###
adv: no need remeber order of the arguments

```python

def func(a, b=5, c=10):
    print('a is', a, 'and b is', b, 'and c is', c)

func(3, 7)
func(25, c=24)
func(c=50, a=100)

```


double quote same as single quote
with triple quotes I can use double or single quote in the string

Strings Are Immutable

####This means that once you have created a string, you cannot change it. Although this might seem like a bad thing, it really isn't. We will see why this is not a limitation in the various programs that we see later on.

String builder = format method
number are optional

age = 20
name = 'Swaroop'

print('{0} was {1} years old when he wrote this book'.format(name, age))
print('Why is {0} playing with that python?'.format(name))
---------------------

output
$ python str_format.py
Swaroop was 20 years old when he wrote this book
Why is Swaroop playing with that python?

string concatenation:
name + ' is ' + str(age) + ' years old'
same but ugly not good practice
 
---------------------
Regex use raw string
use r at the front

Always use raw strings when dealing with regular expressions. Otherwise, a lot of backwhacking may be required. For example, backreferences can be referred to as '\\1' or r'\1'.


```python
can have else in while loop
while running:
    guess = int(input('Enter an integer : '))

    if guess == number:
        print('Congratulations, you guessed it.')
        # this causes the while loop to stop
        running = False
    elif guess < number:
        print('No, it is a little higher than that.')
    else:
        print('No, it is a little lower than that.')
else:
    print('The while loop is over.')
    # Do anything else you want to do here

print('Done')

```

---------------------------
in C/C++, if you want to write for (int i = 0; i < 5; i++), then in Python you write just for i in range(0,5)

---------------------
global keyword  declare that a variable is global
so inside each function variable can still be changing
