Liatrio is Hiring.
Complete our DevOps Challenge for a prize! challenge.liatr.io
Internships : tinyurl.com/liatrio20

BBQ Oct 18th at Noon (Liatrio office, 530 Broadway)


VSCode plugin : remote something or other.

python/django :

from django.shortcuts import render
from django.http import HttpResponse

# Create your iews here.
def index(request):
  return HttpResponse("Something.")
  
python:

settings.py has an area called TEMPLATES

make new directory named templates
in that template folder make something "base.html"



from django.shortcuts import render
from django.http import HttpResponse

```# Create your views here.
def index(request):
#?
  return render(request, "base.html") 
#?

This will send a webpage based off of the code.

What we want to do is to pass some context to render.
(add at the beginning under the def, it will be key and variables)
context={
  "variable":"Hello World"
}

In the HTML file, you can define a variable

{{ variable }}


Change return to
  return render(request, "base.html", context=context)

And it will print out the variable.


<ul>
{% for o in some_list %}
<li>{{o}}</li>
{% endfor %}


m=20
n=10
a=[]
for i in range(m):
  b=[]
  for j in range(n):
    b+=[j]
  a+=[b]
```

random BS code


```index.html can be
{% extends base %}
{% include other stuff %}
```

*Foundation Code*
is a library for stuff
look at docker-compose for errors.
pathing doesn't work in django just by having it in the right folder.

*What are these files*?

Look at documentation :
look at static documentation (staticfiles_storage)
We need
```{% load static %}
<img src="{ % static "my_app/example.jpg" %}", alt="My Image" %}

add the "{ static "/file/path" %}"
```



