# Ex.05 Design a Website for Server Side Processing
## Date:15.05.25

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

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
<!DOCTYPE html>
<html>
<head>
  <title>Power Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
      max-width: 400px;
      margin: auto;
    }
    input, button {
      padding: 10px;
      margin-top: 10px;
      width: 100%;
    }
    #result {
      margin-top: 20px;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <h2>Power Calculator</h2>
  
  <label for="voltage">Voltage (V):</label>
  <input type="number" id="voltage" placeholder="Enter voltage in volts">

  <label for="current">Current (I):</label>
  <input type="number" id="current" placeholder="Enter current in amperes">

  <button onclick="calculatePower()">Calculate Power</button>

  <div id="result"></div>

  <script>
    function calculatePower() {
      const voltage = parseFloat(document.getElementById('voltage').value);
      const current = parseFloat(document.getElementById('current').value);

      if (isNaN(voltage) || isNaN(current)) {
        document.getElementById('result').innerText = 'Please enter valid numbers for both voltage and current.';
        return;
      }

      const power = voltage * current;
      document.getElementById('result').innerText = `Power = ${power.toFixed(2)} watts`;
    }
  </script>

</body>
</html>

views.py

from django.shortcuts import render

def calculate_power(request):
    Power = None
    if request.method == "POST":
        try:
            Volt = float(request.POST.get("num1"))  
            Current = float(request.POST.get("num2"))  
            Power = Volt * Current
            print(f"Voltage: {Volt}V, Current: {Current}A, Power: {Power}W")
        except (TypeError, ValueError):
            Power = "Invalid input"
    return render(request, 'powerapp/power.html', {'Power': Power})

urls.py

from django.contrib import admin
from django.urls import path
from powerapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.calculate_power, name='calculate_power'),
]

```



## SERVER SIDE PROCESSING:


![image](https://github.com/user-attachments/assets/18784169-69ad-43cd-a91f-1896ee04b413)


## HOMEPAGE:


![image](https://github.com/user-attachments/assets/68f97fb9-ec8f-4dcf-89ef-a539ac1b5788)


## RESULT:
The program for performing server side processing is completed successfully.
