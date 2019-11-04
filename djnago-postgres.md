# Use Postgresql with django application
Commands to install and configure PostgreSQL to use with Django applications

## Prerequisites: install `pip`, `postgresql` etc. in the systems
```bash
sudo apt-get update
sudo apt-get install python-pip python-dev libpq-dev postgresql postgresql-contrib
```

## Create Database and User

**Change to `postgres` user**
```bash
sudo su - postgres
```
**Start shell session**
```bash
psql
```
**Create Database**
```bash
CREATE DATABASE myproject;
```
**Create Database User**
```bash
CREATE USER myprojectuser WITH PASSWORD 'password';
```
**Modify Connection Parameters `client_encoding`, `default_transaction_isolation` and `timezone`**
```bash
ALTER ROLE myprojectuser SET client_encoding TO 'utf8';
ALTER ROLE myprojectuser SET default_transaction_isolation TO 'read committed';
ALTER ROLE myprojectuser SET timezone TO 'UTC';
```
**Give access rights to database user**
```bash
GRANT ALL PRIVILEGES ON DATABASE myproject TO myprojectuser;
```
**Exit sql prompt**
```bash
\q
```
**Exit postgres session**
```bash
exit
```

## Configure the Django Database Settings

```bash
. . .

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'myproject',
        'USER': 'myprojectuser',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '',
    }
}

. . .
```

### Use Database URL
```bash
pip install dj-database-url
```
**settings.py**
```bash
import dj_database_url

DATABASES['default'] = dj_database_url.config(
    default=postgres://myprojectuser:password@localhost:5432/myproject, 
    conn_max_age=600
)
```

### For more details
[How To Use PostgreSQL with your Django Application](https://www.digitalocean.com/community/tutorials/how-to-use-postgresql-with-your-django-application-on-ubuntu-14-04) 

[DJ-Database-URL](https://github.com/jacobian/dj-database-url)