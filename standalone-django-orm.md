# Using Standalone Django ORM for Database operations
How to use django orm only for a database management project. We used `pipenv` to create virtual environment. Here we focused using only `postgresql` database.

- ### Clone this repository
```bash
git clone https://github.com/masnun/django-orm-standalone.git
cd django-orm-standalone/
```
- ### Delete `requirements.txt` file

- ### Create virtual environment
```bash
# you can choose other ways rather than using pipenv 
# to create virtual environment

pipenv install --python 3
```

- ### Activate virtual environment
```bash
pipenv shell
```

- ### Install `Django`, `psycopg2` and `dj-database-url`
```bash
pipenv install django
pipenv install psycopg2
pipenv install dj-database-url
```

- ### Generate Secret key, Link: [secret key generator]((https://djecrety.ir/))

- ### Change Secret Key in `settings.py`
```bash
SECRET_KEY = "replace_with_generated_key"
```
- ### Create database in postgresql [help link](https://github.com/Ishtiaq11/mydjango/blob/master/djnago-postgres.md)

- ### Modify Database Configuration in `settings.py`
```bash
# Comment out other database settings
import dj-database-url

DATABASES = {}
DATABASES['default'] = dj_database_url.config(
    default="postgres://dbuser:password@host:port/dbname", 
    conn_max_age=600
)
```
- ### Open "data/models.py". Modify existing model or add your own

- ### Run `python manage.py makemigrations` to make migration scripts

- ### Run `python manage.py migrate` to create the tables and sync db changes. Feel free to use other manage.py commands available for django orm.

- ### Every time you make changes to models or change db parameters, don't forget to run the migrations.

- ### Change or Modify `main.py` according to your needs

### Links
[Django ORM Standalone Application](https://github.com/masnun/django-orm-standalone)
