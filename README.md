# EX.No: 03 DEVELOP A DJANGO-BASED CRUD APPLICATION
## Date:15.11.2026
## AIM

To develop a Django-based web application that performs CRUD (Create, Read, Update, and Delete) operations on student records.

## ALGORITHM

1. Create a Django project and an application.
2. Define the `Student` model with the required fields (Name and Email).
3. Run migrations to create the database table.
4. Configure URL routing for Home, Add, Update, and Delete operations.
5. Create the `home()` view to retrieve and display all student records.
6. Create the `add()` view to insert a new student record into the database.
7. Create the `update()` view to modify an existing student record using its ID.
8. Create the `delete()` view to remove a student record using its ID.
9. Design the HTML page with separate forms/buttons for Add, View, Update, and Delete operations.
10. Run the Django development server and perform all CRUD operations through the web browser.

## PROGRAM
```
views.py
from django.shortcuts import render

def calculate_churn_rate(request):
    context = {}
    
    if request.method == "POST":
        initial_str = request.POST.get("Initialcust", "0")
        present_str = request.POST.get("Presentcust", "0")
        
        Initialcust = int(initial_str) if initial_str else 0
        Presentcust = int(present_str) if present_str else 0
        
        if Initialcust > 0:
            churn_rate = ((Initialcust - Presentcust) / Initialcust) * 100
        else:
            churn_rate = 0
            
        # This will output the calculated value directly in your terminal
        print("Calculated Churn Rate:", round(churn_rate, 2), "%")
            
        context = {
            "Initialcust": Initialcust,
            "Presentcust": Presentcust,
            "churn_rate": round(churn_rate, 2),
        }
            
    return render(request, "app/calc.html", context)
# Create your views here.

urls.py
from django.contrib import admin
from django.urls import path
from app import views

urlpatterns=[
    path('admin/', admin.site.urls),
    path('',views.calculate_churn_rate,name='calculate_churn_rate'),
]

calc.html
<html>
    <head>
        <title>
            CHURN_CALCULATOR
        </title>
    </head>
    <body>
        <h3>ARVIND-26017022</h3>
        <form method="POST">
            {%csrf_token%}
            <label>Initial Customer:</label>
            <input type="number" name='Initialcust' value="{{Initialcust}}"><br><br>
            <label>Current Customer:</label>
            <input type="number" name="Presentcust" value="{{Presentcust}}"><br><br>
            <input type="submit" value="calculate">
            <input type="reset"><br><br>
            <label>Churn Rate:{{churn_rate}}%</label>
        </form>
    </body>
</html>
```


## OUTPUT
web server
![alt text](<Screenshot (27).png>)
web page
![alt text](<Screenshot (28).png>)

## RESULT

A Django-based CRUD web application was successfully developed to perform Create, Read, Update, and Delete operations on student records using SQLite as the backend database.


