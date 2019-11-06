Using Standalone Django ORM in your Application
===============================================

How to setup?
-------------
+ git clone the [source](https://github.com/Ishtiaq11/django-orm-standalone.git) as a starting point
+ Change to your project directory
+ Create a new python3 virtualenv: `python3 -m venv .env`
+ Activate the virtualenv: `source .env/bin/activate`
+ Install Dependies: `pip install -r requirements.txt`

How to use?
-----------
+ Generate a new `SECRET_KEY` for your settings.py.
+ Create and Modify `.env` file to add your database connection parameters (See ".envs/.postgres" for examplle).
+ Open "data/models.py". Modify existing model or add your own.
+ Run `python manage.py makemigrations` to make migration scripts
+ Run `python manage.py migrate` to create the tables and sync db changes. Feel free to use other manage.py commands available for django orm.
+ Every time you make changes to models or change db parameters, don't forget to run the migrations.
