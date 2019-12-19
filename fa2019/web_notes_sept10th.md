We covered dockerization and stuff.
Do virtual environment.
Figure out virtual environment.


Homework --> Due this weekend.
This is good to know.

try:

except:

Example Class:
class MyClass:
  """A simple example class"""
  //Default __init__
  def __init__(self):
  self.data = []
  self.i = 12345

  i = 12345
  def f(self):
    self.bob = 4
    return 'hello world' + str(self.i)


Django : 

pip freeze > requirements.txt

docker-compose up

django-admin
one explicit one to use : django-admin startproject mysite

docker on linux runs as root,
something you can do to fix that :
docker-compose user/id-group
in the requirements file, you can define the user in

web : 
  user : "UID:GID" on Ubuntu if no other users 1000:1000

