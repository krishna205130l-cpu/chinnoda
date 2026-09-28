def food(tos):
    dish_list=dish.objects.all()
    context = {
        "dish_list":dish_list
    }
    return render(tos,"myapp/index.html",context)

def specifics(request,id):
    Dish=dish.objects.get(id=id)
    context= {
        "Dish" : Dish
    }
    return render(request,"myapp/r1.html",context)

def add_menu(request):
    form=FoodForm(request.POST or None)
    if request.method=="POST":
        print("POST request is triggered")
        print(request.POST)
        if form.is_valid():
            form.save()
            return redirect('myapp:food')


    form=FoodForm()
    context={
        'form': form
    }
    return render(request,"myapp/food.html",context)

this is r1.html
-->{% extends 'myapp/b2.html' %}
{% block body %}
    <div class="m-10 flex">
        <div>
            <img class="w-64 rounded-lg" src="{{Dish.dish_image}}" alt="">
        </div>
        <div class="mx-10 space-y-2">
            <div class="font-bold">{{ Dish.dish_name }}</div>
            <div>{{ Dish.dish_desc }}</div>
            <div class="text-blue-600 font-bold">${{ Dish.dish_price }}</div>
            <div>
                <a class="bg-green-500 px-4 py-2 rounded-md font-bold text-white" href="">Edit</a>
                <a class="bg-red-500 px-4 py-2 rounded-md font-bold text-white" href="">Delete</a>
            </div>
        </div>
    </div>
{% endblock %}


this is base.html
-->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <title>Document</title>
</head>
<body>
    <nav class="bg-blue-600 text-white">
        <div class="flex justify-between px-2 py-4">
            <a href="">Mobile-Store</a>
            <div class="space-x-4">
                <a href="">Contact</a>
                <a href="">About</a>
                <a href="">About us</a>
            </div>
        </div>
    </nav>
    {% if messages %}
        {% for message in messages %}
            <div class="bg-green-500 text-white p-4">
                {{ message }}
            </div>
        {% endfor %}
    {% endif %}
   

    {%block body%}

    {% endblock%}


this is index.html
-->
{%extends "myapp/b2.html" %}
{% block body%}
    <div>
        {%for dish in dish_list%}
        <div class="m-10 flex">
            <div>
                <img class="w-64 rounded-lg" src="{{dish.dish_image}}" alt="">
            </div>
            <div class="mx-10">
                <div class="font-bold">{{dish.dish_name}}</div>
                <div>{{dish.dish_desc}}</div>
                <div class="text-blue 600 font-bold">${{dish.dish_price}}</div>
            </div>
            <div>
             <a class="bg-red-500 px-4 py-2 rounded-md font-bold text-white" href="/myapp/specifics/{{dish.id}}">View details</a> 
            </div>
        </div>
        {%endfor%}
    </div>
{% endblock %}

these are the urls i used

urlpatterns = [
    path('',views.greet),
    path('detail/<int:id>/',views.detail),
    path('food/',views.food,name="food"),
    path('prices/',views.prices,name="prices"),
    path('specifics/<int:id>/',views.specifics,name="specifics"),
    path('add/',views.add_mobile,name="add_mobile"),
    path('update/<int:id>/',views.update_item,name='update_item'),
    path('enter/',views.add_menu,name='add_menu'),
   

]
