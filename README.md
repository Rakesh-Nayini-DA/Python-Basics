# Python-Basics

OOPS

instance variable (in __init__)
class variable (at class level, ClassName.variable=uptadedValue it reflects in all objects)

instance method (self)
calss method (cls) @classmethod
static method (no need of passing scope)@staticmethod

inner class (you can create object to instace variable to the outer class)

inheritance (ChildClass(ParentClass) sigle,multiple,multilevel)

constructor in inheritance:
1. uses child class init if exists else considers parent init
2. we can call using super().__init__() for parent constructor 
3. Method Resolution Order (MRO) left to right
super()~super calss

Polymorphism (multiple forms of object):
1. Duck Typing (Having same method in different objects for the refernce at another place. IDE example from Telusko, same like interfaces in Java)
2. Operator Overloading (adding operator (like +,-.. or any standard methods inbuilt)method for custom obejcts to support actions in our format or support same as like for standard objects)
3. Method Overloading (There is no direct support for this, you need to check number of args provided in input by passing default value=None)
4. Method Overriding (Overrinding the child class method with same name as parent method for customization purpose)

Abstract Classes and Methods:
1. method with declaration not defination. Python not supprots Abstarct classes.
2. we can create by using import ABC module with @abstractmethod
3. Best practices in Oops to use Abstarct


Iterator (like purpose i++)
iter(list) use __next__
for i in list (calls __next__ method in that list object)
to stop for loop use raise StopIteration
if you call iter next above the loop, then it will continue from next element
We can create custom iter using class with method overloading like operator (i.e __iter__, __next__)

Generators (iterator by Python)
Using yield instead of return in simple method will creates a Generator

Decoraters:
To add/change behaviour of existing function
Pass the main function to decorator function, add the logic in inner function, then run the main input function with updated logic of inputs
eg: div_new = smart_div(div) then call div_new insttead of div

Exception Handle:
try/except/finally (always runs)
try/except/else (else runs if no error)
Use finally for connection closing like similar actions
except([exp1,exp2,...])
raise used to Exception
raise [Exception [, args [, traceback]]]
#define Python user-defined exceptions
class Error(Exception):
   """Base class for other exceptions"""
   pass
 
class InputTooSmallError(Error):
   """Raised when the entered alpahbet is smaller than the actual one"""
   pass
 
class InputTooLargeError(Error):
   """Raised when the entered alpahbet is larger than the actual one"""
   pass



Multi threading: search again about multiprocessing
It will be achieved by using in built threading modules using start and join methods.

File Handle:
Use open method for file opening/creating 
open('filename','access') # in access ('r' refers readonly, 'w' is write only (it overrides everytime), 'a' is append used for update)
use methods like read, write, readline,...
use for loop for read all data and write in other file so....
USE 'rb', 'wb' for read and write binary data (like images, videos...)

Search about globals() and locals()

Python interpreter or Compiler?

Source code--> Compiler --> Byte Code --> Interpreter/PVM --> Machine language
Python concept done implemetation in multiple ways (Cpython, PyPy, IronPyhon, Jython), widly used one is Cpython.

Searching in Python:

Linear Search: just compare search element one by one in list until it found like using while or for loop.

Binary Search: it is quite faster than linear search. it only works when list is sorted. use lower amd upper bound concept. find value by using mid=(lower+upper)//2. if value is lessthan the search value increase lower bound else deacrease the lower bound until to find the element.

Sorting in Python: workes on Swapping concept

Bubble Sort: need to swap largest number to last index everytime. that means it has length-1 iterations to complete sorting for a list. Use two for loops. one for iteration range. second to compare elements. swap by storing in temp variable.

Selection Sort: find the min value by starting with first index. then replace min pos with current index value. decrease the unsroted list length by 1. continue the same process using 2 for loops. one for iterations and other for iterating unsorted list.

Zip Function: to join to lists into single or iter at a time

Socket Programming: We can create cleint and server architechture using socket module. using some binding and other methods to handle.

Django:

It is a open source framework (combination of components and packages)
Follows MVT like MVC
It is fast, budled with components like DB, login..., Security and Scalability

Setup: Install latest Python and upgrade to latest pip version, crete a virtual env. then install Django

1. django-admin startproject projectName
2. It creates a files like manage.py for empty django project with required structure
3. python manage.py runserver

In Django apps are multiple in Project
manage.py, urls.py, settings.py, wsgi.py comes under project

python manage.py startapp appName

views.py,apps.py, models.py... comes under app

You can create app level urls.py file for isolation, then join in main urls.py using include function

to route path to logic, you can use method or class in a veiws.py file. path('/home',views.home (use views.className.as_view))

templates are used to render frontend content. create a template folder at project level, join in settngs.py using os.join at 'DIRS'

request.GET and .POST is used to get data from respective method. if you use POST req for path. you need to pass csrf_token in form 

use templates folder for .html files join if only at project level else app level
create static folder and join in settings
use python manage.py colletstatic used to collec app level static files to root level
use render to return html page and pass the data in dict format to use in Jinja

IMP: Add app name in INSTALLED_APPS in settings.py
ORM (table from a CLASS):
Object Relation Manager; using class with variable to create table with models

Model Migrations:

Create a Class with table name with inheriting models.Model. 
create fields like name=models.CharField(max_length=100)

type cmd: python manage.py makemigration

cmd2: python manage.py sqlmigrate appName migrationFileName (It creates SQL query)

cmd3: python manage.py migrate

Re-Migration:
Alter table with SQL
or
python manage.py makemigration

python manage.py migrate


Django Admin:

create super user:

cmd: python createsuperuser:
enter details

login with super user at /admin

Goto admins.py import table model from models
then admin.site.register(tableName)

It will create a ability to add rowa to that table from admin page

Add//fetch data from Admin page:

Use MEDIA_ROOT and MEDIA_PATH for images storing and register url in url.py

you can add data from admin page and it will refelects in DB

USER Registration:
Create a sample form to insert data into django.USER table fields
Save the data to user.objects.create_user(fields=.....)

uses module messages.info... for alerts and validations

USER Login/Logout:

Create login.html with form...

get the username and password from POST req.

Use auth module auth.authunticate(username=username,password=passowrd) it checks auth.
If user exists then auth.login(request,current_user) then redircts to home page.

Use jinja {{ if user.is_authunticated }} for showing register/login pages else show logout page

Use auth.logout(request) to logout current user. redirect to login page, that's it.

Check user.is_authunticated for preventing access to pages in enitre app.


Data Structures: used to organize data in manner

1. Built in DS's (list, set, tuple, Dict)
2. User defind DS's (Stack, queue, Tree, linkedList, Graph, HashMap)

Lists: Different data types of data in sequential order and Mutable

Tuple: Faster than list and immutable. we can't add data after object creation and not indexed

Dict: key value pair and mutable

Set: Un-ordered data with unique elements and Mutable

Stacks: LIFO, linear ds's. pushing and popping supperts

Queue: FIFO, uses in job scheduels

Trees: non linear, follows roots and nodes eg: HTML...

Linked List: linear and linked with pointers, used in music player apps...

Graph: used for dashboards

HashMap: Same like Dict

Algorithems: rules or formula and conditions for a solution

Step by setp instructuions 
each step depends on prevous step

Sorting algorithems:
Merge, bubble, insertion, selection, shell sort

enumarate(): to get index and values at a time like
Months = ["Jan","Feb","Mar","April","May","June"]
for i, m in enumerate (Months):
        print(i,m)


Flask:

Configuration part will be
from flask import Flask

app = Flask(_name_)

View part will be
@app.route("/")

Def hello():

return "Hello World"

While you model or main part will be
app.run(debug = True)


There are two parameters passing mechanism in Python:

Pass by references
Pass by value
