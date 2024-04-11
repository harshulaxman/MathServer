# Ex.05 Design a Website for Server Side Processing
## Date:05/04/2024

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
math.html 

<!DOCTYPE html>
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Area of right cylinder</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body {
    background-color: rgb(175, 199, 243);
}
.edge {
    width: 100%;
    padding-top: 190px;
    text-align: center;
}
.box {
    display: inline-block;
    border: thick dashed rgb(45, 111, 77);
    width: 520px;
    min-height: 320px;
    font-size: 18px;
    background-color: rgb(134, 209, 160);
}
.formelt {
    color: black;
    text-align: center;
    margin-top: 7px;
    margin-bottom: 8px;
}
h1 {
    color: rgb(98, 68, 162);
    padding-top: 25 px;
}
</style>
</head>
<body>
<div class="edge">
    <div class="box">
        <h1>Surface Area of Right Cylinder</h1>
        <h3>Harsshitha lakshmanan (212223230075)</h3>
        <form method="POST">
            {% csrf_token %}
            <div class="formelt">
                Radius: <input type="text" name="radius" value="{{r}}">m<br/>
            </div>
            <div class="formelt">
                Height: <input type="text" name="height" value="{{h}}">m<br/>
            </div>
            <div class="formelt">
                <input type="submit" value="Calculate"><br/>
            </div>
            <div class="formelt">
                Area: <input type="text" name="area" value="{{area}}">m<sup>2</sup><br/>
            </div>
        </form>
    </div>
</div>
</body>
</html>

urls.py 

from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('surfacearea/',views.surfacearea,name="surfacearea"),
    path('',views.surfacearea,name="surfcaearea")
]

views.py

from django.shortcuts import render
def surfacearea(request):
    context = {}
    context['area'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        print('request.POST:', request.POST)
        r = request.POST.get('radius', '0') 
        h = request.POST.get('height', '0') 
        print('radius =', r)
        print('height =', h)
        area = 2 * 3.14 * int(r) * int(h) + 2*3.14*int(r)*int(r)
        context['area'] = area
        context['r'] = r
        context['h'] = h
        print('Area =', area)
    
    return render(request, 'mathapp/math.html',context)


```

## SERVER SIDE PROCESSING:
![Screenshot 2024-04-05 141021](https://github.com/harshulaxman/MathServer/assets/145686689/2db8b314-4947-456a-88d1-7504f41d3069)


## HOMEPAGE:
![Screenshot 2024-04-05 140717](https://github.com/harshulaxman/MathServer/assets/145686689/b7fa3f6c-49ef-4c21-acb8-257ee39ba0f7)


## RESULT:
The program for performing server side processing is completed successfully.
