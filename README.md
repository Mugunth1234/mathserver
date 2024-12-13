# Ex.05 Design a Website for Server Side Processing
# Date:
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
```
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

```
# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
math.html
```
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Power of a lamp</title>
    <style>
        body {
            background-color: rgb(2, 178, 64);
            font-family: 'Lora', serif;
        }
        .container {
            width: 400px;
            margin: 50px auto;
            text-align: center;
            background-color: rgb(23, 206, 212);
            color: rgb(60, 19, 222);
            padding: 20px;
            border: 3px dashed rgb(3, 16, 19);
            border-radius: 10px;
        }
        input[type="text"] {
            width: 80%;
            padding: 5px;
            margin: 10px 0;
        }
        input[type="submit"] {
            padding: 5px 10px;
            background-color: rgb(189, 196, 12);
            color: rgb(248, 246, 246);
            border: none;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="container">
    <h1>Power of a lamp</h1>

    <form method="POST">
        {% csrf_token %}
        <label for="intensity">Intensity (I in Amps):</label>
        <input type="text" name="intensity" id="intensity" required><br><br>

        <label for="resistance">Resistance (R in Ohms):</label>
        <input type="text" name="resistance" id="resistance" required><br><br>
        <font ="red">
        <button type="submit"><b>calculate</b></button>
    </font>
    </form>

    {% if power is not None %}
        <h2>Calculated Power: {{ power }} Watts</h2>
    {% endif %}
</div>
</body>
</html>

          
```
views.py
```
from django.shortcuts import render

def power_calculator(request):
    power = None  

    if request.method == 'POST':
        
        intensity = request.POST.get('intensity')
        resistance = request.POST.get('resistance')

        
        if intensity and resistance:
            try:
            
                I = float(intensity)
                R = float(resistance)
                power = I**2 * R
                print('intensity=',I)
                print('resistance=',R)
                print('power=',power)  

            except ValueError:
                power = "Invalid input. Please enter numerical values."

    
    return render(request, 'mathapp/math.html', {'power': power})
```
urls.py
```
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.power_calculator, name='power_calculator'), 
]
```
# SERVER SIDE PROCESSING
![Screenshot 2024-12-05 200209](https://github.com/user-attachments/assets/f784850e-e6a2-414a-990f-6db84fec5d50)

# HOMEPAGE:
![Screenshot 2024-12-13 160429](https://github.com/user-attachments/assets/c74ac1a7-cbef-416f-baaf-f49969f30d00)

![Screenshot 2024-12-05 200147](https://github.com/user-attachments/assets/c6b75614-718d-4698-ab77-e21c35272f38)


# RESULT:
The program for performing server side processing is completed successfully.
