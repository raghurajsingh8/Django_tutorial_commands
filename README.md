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
_____________________________________chapter 8 Python django structure---57.17-----------------------

