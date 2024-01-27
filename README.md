# Django_tutorial_commands total 53 chapter

----------------------------------chatpter 1 INTRODUCTION----------------------------------------
Django is python framework for web devlopment
Framework is pre build set of rules,idea,structure of website
Follows the MVT model-view-template

company using django 
YOUTUBE INSTAGRAM DISQUS SPOTIFY  MOZILA 

----------------------------------chatpter 2 PREREQUISITE---------------------------------------

PYTHON HTML CSS JS

----------------------------------chatpter 3 MVT---------------------------------------
MODEL VIEW TEMPLATE 

==>SOFTWARE DESIGN PATTERN
==>MODEL:-MODEL IS GOING TO ACT AS THE INTERFACE OF YOUR DATA   (DATABASE) 
==>VIEW:-USER INTERFACE   (VIEW) 
==>TEMPLATE:-A TEMPLATE CONSISTS OF STATIC PARTS OF THE DESIRED HTML OUTPUT AS     SOME SPECIAL SYNTAX DESCRIBING HOW DYNAMIC CONTENT WILL BE INSERTED.  (HTMLFILE) 

                             |<-------->MODEL
USER<--->DJANGO<---->URL<---->VIEW-|
                             |<-------->TEMPLATE


----------------------------------chatpter 4 INSTALLATION---------------------------------------
PIP :-DEPENDENCY MANAGER
INSTALATIION EASY

----------------------------------chatpter 5 NEW PROJECT SETUP ---------------------------------
________________________________________________________________________________________________
__"django-admin"likhenge to avilable subcommands show hoga"__
    check
    compilemessages
    createcachetable
    dbshell
    diffsettings
    dumpdata
    flush
    inspectdb
    loaddata
    makemessages
    makemigrations
    migrate
    optimizemigration
    runserver
    sendtestemail
    shell
    showmigrations
    sqlflush
    sqlmigrate
    sqlsequencereset
    squashmigrations
    startapp
    startproject
    test
    testserver
    _____________________________________________________________________________________________
__"pip freeze"__

asgiref==3.7.2
certifi==2023.11.17
distlib==0.3.8
Django==4.2.7
filelock==3.13.1
numpy==1.26.3
pipenv==2023.11.15
platformdirs==4.1.0
psycopg2==2.9.9
psycopg2-binary==2.9.9
setuptools==69.0.3
sqlparse==0.4.4
tzdata==2023.3
virtualenv==20.25.0

cd to next folder change director
_________________________________________create project_____________________________
django-admin startproject __yourappname__
app bn jayega



-------------------------------------chapter 6 Srarting a Development Server------------------------
__python manage.py runserver__

tb code chalega
ctrl C to stop the server 

____________________________apne port pr server chalane ke liye___python manage.py runserver 1234________


___________________________________chapter 7_________install vs code __________________________
done
_____________________________________chapter 8 Python django structure--------------------------
filewasdeleted
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
x                                                                              x
x                      deleted  x x x x x  x   x x x   xx x x x  x x           x 
x                                                                              x
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

------------------------------------------chapter 9 migrate to open admin---------------------------------
__python manage.py migrate__ to sqlite vali file me kuch aa jayenga aur okokok krke 18 error solve kregaaur admin agar nhi khul rha h to khulega ab

-----------------------------------chapter 10 install sqllite--------------------------
install krke app ke sqlite ko kholenge to 11 tables aur 15 indices phle se hi honge
-----------------------------------------chapter 11 create superuser--------------
python manage.py createsuperuser
ask many qyestion give it
you can check in sqllite auth_user table 
________________________________chapter 12 URLS & VIEWS________________________________
 /BLOG aise krke alag alag page khol skte h jo aapas me link rhete ha i 

 urls.py me sare urls
 view.py me saare view 

 ye dono aapaas me jude hue honge 
 ------------------------chapter 13 creating urks and views---------
step 1===> main folder aone aap urls.py apne aap bne rhega  isi ka brother file create krenge 
          main folder ke andar hi views.py
step 2===>views.py me-------
          from django.http import HttpResponse

          def aboutus(request):
              return HttpResponse("Welcome to my world")

step 3===>urls.py me----------
           from yourfoldername import  views 
           urlpattern me ==>
           path('aboutus/',views.aboutus)


           **jo django home page khul rha th ashayad vo ab na khule**


-------------------------------chapter 14 create dynamic url--------------------------

page vhi rhtA CONTENT BADALTE RHTA HAI 

DYNAMIC ROUTE KAISE BNAYENGE 
ye 3 base per bn skta h
int 
str










slug   hello-ws-tech    ,word + das

task==> dynamic data pr page bdle,, yaani raj url likhe to raj aaye ,shalini likhe to shalini aaye aaye haaye,5 likhe to 5 aaye 4 likhe to 4 aaye


urls.py==============>>>>>>>>>>>>>>>>>>>>>>
   path('course/<int:courseid>',views.coursedetail)
views.py============>>>>>>>>>>>>>>>>>>>>>
def coursedetail(request,courseid):
                  return HttpResponse(courseid)

url inpt http://127.0.0.1:8000/course/9       output 9 
for string
   path('course/<str:courseid>',views.coursedetail)
   url inpt http://127.0.0.1:8000/course/raj       output raj 
same for slug

   agar str int kuch define na kre to valid rhega teeno keliye
path('course/<courseid>',views.coursedetail)


-----------------------------------------chapter 15 Render a HTML template as response------
step 1===>templates nama ke folder bnayenge
step 2==>index.html bnayenge kuch likhenge
step 3==>setting.py me directry set krenge
 line 54          TEMPLATES me jayenge 'DIRS': [BASE_DIR,"templates"],

 step 4==>views.py   from django.shortcuts import render
step 5 views.py         def homepage(request):
                        return render(request,"index.html") 
step 6==>urls.py me     path('', views.homepage),

to index html ka content shsow hoga home page pr

----------------------------------------------chapter 16 passing data from a django view to Template-----------------
__step1__
views.py

def homepage(request):
data={
'title':'Leaonths',
'name':'raghuvraj'}
        return render(request,"index.html",data)
__step2__index.html me
key paass krenge
<title>{{title}}</title>
<h3>{{name}}</h3>

-----------------------------------------chapter 17 loop in django--------------------
        
data me list bnayenge aur use show krne ke liye loop use hoga 
data={
'list':['python','c++','java'],
}
index.html me

{% for i in list  %}
<div>{{forloop.counter}}{{i}}</div>
{% endfor %}

 
forloop.counter==>1 2 3 4 5 6 7 numbering krega
forloop.counter0==> 0 1 ,0 se start krega 
forloop.revcounter==>3 2 1
forloop.revcounter0==>2 1 0
forloop.first==>true false false fal.....


========================show dictionalry =========================
view.py me data={

'student_details':[
{'name':'pradeep','phone':'83170727289'},
{'name':'raghv','phone':'94514623783473'}]

}

index.html me
<table border="2">
    <tr>
 <th>name</th>
 <th>phone</th>
    </tr>
    {%  for d in student_details  %}
    <tr>
      <td>{{d.name}}</td>
    <td>{{d.phone}}</td>   =====>% nhi rhega 
    </tr>
 {%  endfor %}
</table>
=============================================chapter 18 if....elif.....else===============
 
task list bnayenge aur keval 5 ,7,11 13 ke devider ko jo 60 se bde h unko print krenge
syntax:-
if========================>
{% if n>20 %}
<div>{{n}}</div>
{% endif %}

if else=======================>

{% if n > 20 %}             > is sign ke aas paaas space rhna jruri h 
<div>{{n}}</div>
{% else %}
<div>{{n-2}}</div>
{% endif %}



list|length use for lengtn 
html me {{_________content___________}}
python me {%______content____________%}


__________________static files_____chapter 19 **** using css js images in django _____________________
task===>ek alag jagah css js image html likha h use django me laana

step 1==>html vali saaari file templates me daaal denge 
step 2==>baaaki ki saaari foldercopy krke static me paste krna hai
step 3==>setting.py me static ki directry set krenge

STATICFILES_DIRS =[
BASE_DIR , "static",]

localhost:8000/stsatic/css/main.css(file name)    to file ka code khul jayega 

html files me jha csslink krayi gyi thi vha ab /static/ jod denge href me path ke liye

agar navbar me index html se 4-5 file jude h phir bhi views,url me sb  me define krna hoga

aur click krne pr page nhi khuega uppper url me hi likhna pdega

 # path('aboutus/',views.aboutus),
     path('contact',views.contact),
    #  path('course/<int:courseid>',views.coursedetail),
    #  path('course/<coursename>',views.coursedetailn)
    path('shop',views.shop),
    path('product',views.product),

    contact/  shop/  product/ likhne me css call nhi ho rha static se 


isliyw without slash likhenge

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++FINALLY STATIC  FILE KRNE AA GYA CSS JS ++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
__________________________chapter 20 Header & Footer__________________________

header aur footer alag alag file bnayenge 

{%  include "header.html %}
{%  include "footer.html    %}

agar page bnana h  to base.html header footer rhega aur beech ka content extends hote rgega

==============================================================================================
              chapter 21 EXTENDS 
=============================================================================================
base.html me.......header footer jod denge aur beech ka content badalte rhta hai 

{%  include "header.html %}

{% block content %}
{% endblock %}

{%  include "footer.html"    %}


aur ab jo content chahiye us file me jaayenge 
{% extends 'base.html' %}
{% block content %}
                 <html>
                        //////    
                  </html>

{% endblock %}



+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
finally ek file rhegi header ,ek footer ,ek base
base me header footer ko include kr lenge base me block content ka jagah rkhenge khali aur jis file ko run krna h usme base file ko extend krenge base ko aur block content me sb kuch likhenge 


_______________Chapter 22 django url , nav bar click and work properly____________________

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>tarika 1<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
 <li><a href="/" class="active">Home</a></li>
                      <li><a href="/shop">Our Shop</a></li>
                      <li><a href="/product">Product Details</a></li>
                      <li><a href="/contact">Contact Us</a></li>
                      <li><a href="#">Sign In</a></li>


aise likhenge href me
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>.tarika 2<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
urls.py me jayenge 
step 1 kuch name de denge 
----------------------------path('aboutus',views.aboutus,name="about"),
step 2
url likhkar name paaas kr dena hai 
href me ={% url 'about'  %}

__________________________________________chapter 23 how to highlight active link in django______
header vali file me 
<li class="{% if request.path  =='/' %}  active{% endif %}">--------
<li class="{% if request.path  =='/about' %}  active{% endif %}">....

main.css me header .active a{

css property
}

done


______________________________________chapter24______F__O__R___M _____________________________
 THERE ARE FEW POPULAR METHODS GET AND POST

__________________________________GET METHOD___________________________________
summary_---_-_-_-_---_url se data bhejta hai ?maek se separate rhta hai 
  |||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||
====>THE GET METHOD SENDS THE ENCODED USER INFORMATION APPENDED TO THE PAGE REQUEST .THE PAGE AND THe EENCODED INFORMATION ARE SEPARATED BY THE ?CHARACTER 

====>https://www.youtube.com/watch?v=6tdfhlIoxOw&t=13198s    IS LINK ME BHI ? MARK HAI 

====>RESTRICYED TO SEND UPTO 1024 CHARACTERS ONLY
====>never use GET methodEigf you have Password or other sensitive information 
====>Cannot be used to send binary data ,like images or word documents ,to the server




   ____________________________POST method____________________________
summary-_-_-_-_-payment ya sensitive information me use kr skte hai image vgera bhi bhej skte
   
====>The post method transfer information via http headers .the information is encoded as described in case of GET method .
=====>does not have any restriction on data size to be sent.
====>Can be used to send ASCII as well as binary data.
====>The data send by POST method goes through HTTP header so security depends on HTTP protocol.
====>By uhsing secure HTTP you can make sure that your information is secure.


______________________________CHAPTER 25______________________________How to Implement Get method


step 1===>jha saari html file h vhi ek new file bnayenge example____userform.html
step 2===>views.py me connect k r lenge
            def userForm(request):
                return render(request,"userform.html")
step 3====>urls.py me
            path('userform',views.userForm),
step 4 ====>create form in userform.html
           

 <form>
    <div>
        <label for="">value1</label>
        <input type="text" name="num1">
    </div>
    <div>
        <label for="">value2</label>
        <input type="text" name="num2">
    </div>
    <div>
         <button type="submit">Save</button>
    </div>
</form>



button ka type submit hi rakhenge 
aur name jrur rakhenge name se hi value ko get krenge  

def userForm(request):
    try:
       n1=int(request.GET['num1'])
       n2=int(request.GET['num2'])
       print(n1+n2)
      #      ye terminal me aayega
    except:
      pass
          

      return render(request,"userform.html")


 n2=int(request.GET['num2'])    iska alternative ye hai 
 n2=request.GET.get('num2')       int to keval string se convert krne liye lga h



======================output kaise le ==============================
bs variable declare krke output me return kra denge

def userForm(request):
    finalans=0
    try:
       n1=int(request.GET['num1'])
       n2=int(request.GET['num2'])
       finalans=n1+n2
      #      ye terminal me aayega
    except:
      pass
          

    return render(request,"userform.html",{'output':finalans})

    aur userform.html me call kr lenge

  <div>
        <label for="">output</label>
        <input type="text" value="{{output}}">
    </div>

    demarit upper url pr saara data show krega aur vhi se output change kr skte hai
___________________________________CHAPTER 26 POST METHOD________________________________
    
CSRF token
use for stopping CSRF

agar form me method="post


likhke previous code run kre to output me 
CSRF verification failed. Request aborted.aayega
userform.html me______________
form method vali line ke neeche likhna hai 

{% csrf_token  %}
views.py  me_________________
request.method=="POST" kr denge
isme di gyi value upper url me show nhi hogi 


_______________________________________________________views.py me
to ye krne se save pr click krne se gayab nhi higa input use dictionary
def userForm(request):
    finalans=0
    data={}
    try:
       if request.method=="POST":
            n1=int(request.POST['num1'])
            n2=int(request.POST['num2'])
            finalans=n1+n2
            data={
                 "n1":n1,
                 "n2":n2,
                 "output":finalans

            }
      #  yournme=n1+n2
      #      ye terminal me aayega
    except:
      pass
          

    return render(request,"userform.html",data)
_______________________________________________________userform.html me
<form method="post">
    {% csrf_token %}
    <div>
        <label for="">value1</label>
        <input type="text" name="num1" value="{{n2}}">
    </div>
    <div>
        <label for="">value2</label>
        <input type="text" name="num2" value="{{n1}}">
    </div>
  
    <div>
         <button type="submit">Save</button>
    </div>
    <div>
        <label for="">output</label>
        <input type="text" value="{{output}}">
    </div> 
  
</form>


_______________________chapter___27__ HOW to redirect Page in Django___________________
  save krne pr next page me jaise login kiye to home page pr gye  

    step1 ==>views.py me    HttpResponseRedirect likhenge first line me jha import krte hai 
    step2==>   n1=int(request.POST['num1'])
               n2=int(request.POST['num2'])
              finalans=n1+n2
              data={
                     "n1":n1,
                 "n2":n2,
                   "output":finalans}
              return HttpResponseRedirect('/contact')

              save p rclick krne ke baad hm phuch jaaaayenge 





agar output bhi le jaaana hai to 

contact.html me
                    hello {{output}} hi

views.py me
                         data={
                 "n1":n1,
                 "n2":n2,
                 "output":finalans

            }
            url="/contact?output={}".format(finalans)
            return HttpResponseRedirect(url)
      #  yournme=n1+n2
-------------upper ke side 
      
def contact(request):
    
       output=request.GET.get('output')

       return render(request,"contact.html",{'output':output})
---------------------------------------------------------------------------------------
ab tak saara done 
----------------------------------------------------------------------------------------
__________________________________chapter 28 HTML FORM ACTION URL IN DJANGO____________

