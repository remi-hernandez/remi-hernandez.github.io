= Python tips
:hp-tags: python, tips

==== What's here ?

Here you will find some tips n tricks around python.

==== List tricks

====== Print a list in one line
[source,python]
----
>>> l = ["a", "b", "c"]
>>> ";".join(l)
'a;b;c'

>>> l = [1, 2, 3]
>>> "".join(str(l))
'[1, 2, 3]'
----

====== Get the last elem or go back in a list
[source,python]
----
l = ["a", "b", "c"] 
print (l[-1]) # Get the last element of the list which will print "c"
print (l[-2]) # Will print "b"
----

====== Get all the odd numbers of a list
[source,python]
----
>>> l = [0, 1, 2, 3, 4, 5]
>>> l[1::2] # start the list at 1 and go +2 on the iterator
[1, 3, 5]
----
====== Reverse a full list
[source,python]
----
>>> l
[0, 1, 2, 3, 4, 5]
>>> l = l[::-1]
>>> l
[5, 4, 3, 2, 1, 0]
----

====== Remove duplicates in a list

Using the builtin set() {Sets are unordered collections of distinct objects} we can remove all the duplicates and to go back in a list we can use the list() function.

[source,python]
----
>>> l1 = [1, 2, 3, 1, 2, 3]
>>> l1 = set(l1)
>>> l1
set([1, 2, 3])
>>> l1 = list(l1)
>>> l1
[1, 2, 3]
----
====== string list to int list in one line
[source,python]
----
>>> l = ["1", "2", "3"]
>>> l = [int(x) for x in l]
>>> l
[1, 2, 3]
----

====== Remove empty string in a list

[source,python]
----
>>> l = ["a", "", "b"]
>>> l
['a', '', 'b']
>>> l = [x for x in l if x]
>>> l
['a', 'b']
----



==== Ternary in python
Added in 2.5 version of python :

[source,python]
----
a = 1
b = 2
result = 0

result = a if a > b else b
print (result) # will print 2 for b

result = a if a < b else b
print (result) # will print 1 for a

#<1>

####

def yes():
	print "yes"
	
def no():
	print "no"
	
yes() if True else no() 
yes() if False else no()

#<2>

----
<1> Will output : 
>  
2
1

<2> Will output :
>
yes
no

==== Syntax * 

The single star * unpacks the sequence/collection into positional arguments.


[source,python]
----
def sum(a, b):
    return a + b

values = (1, 2)

s = sum(*values) # will return the sum of 1 and 2
----

==== Multilines import

A nice way to import

[source, python]
----
from Package.class import(
        method1,
        method2,
    )
----

==== How to check if a file with extension .xx is in a folder

[source, python]
----
from os import listdir
from os.path import isfile, join

lFilesList = [f for f in listdir(self.__fileName) if isfile(join(self.__fileName, f)) and (join(self.__fileName, f)).endswith(".sda")]
if len(lFilesList) > 0:
   print "There are files"
----

==== Get items from a list a if not in b

Use set(b) instead of b, why ? 
List membership testing is O(n), Set membership testing is O(1)

So if you test list membership in a loop the overall loop is O(n2).

[source, python]
----
a = [1, 2, 3, 4 ,5]
b = [4, 5, 6, 7]

res = [x for x in a if x not in set(b)]

# now res is : [1, 2, 3]
----

==== How to check the method existing in a python object

[source, python]
----
[method_name for method_name in dir(object)
 if callable(getattr(object, method_name))]
----

==== Format text

[source, python]
----

>>> s = "hello world"
>>> s.center(40)
>>> '              hello world               '

>>> '{:*^50}'.format('sample text')
'*******************sample text********************'     # * is the fill character.

>>> '{:^50}'.format('sample text')
'                   sample text                    '     # with a length of 50.

>>> x = 13.949999999999999999
>>> x
13.95
>>> g = float("{0:.2f}".format(x))
>>> g
13.95
>>> x == g
True
>>> h = round(x, 2)
>>> h
13.95
>>> x == h
True
----

==== script with arguments

Use click library : http://click.pocoo.org/5/


