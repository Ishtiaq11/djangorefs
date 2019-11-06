Create Postgresql database for django application
=================================================

Install Prerequisites
---------------------

```bash
sudo apt-get update
sudo apt-get install python-pip python-dev libpq-dev postgresql postgresql-contrib
```

Create Database commands
-------------------------
```bash
# Enter psql shell
sudo su - postgres
psql
```
```bash
# create database
CREATE DATABASE <dbname>;
# create user
CREATE USER <dbuser> WITH PASSWORD <'password'>;
# configuration for django to increse efficiency
ALTER ROLE <dbuser> SET client_encoding TO 'utf8';
ALTER ROLE <dbuser> SET default_transaction_isolation TO 'read committed';
ALTER ROLE <dbuser> SET timezone TO 'UTC';
# grant privileges
GRANT ALL PRIVILEGES ON DATABASE <dbname> TO <dbuser>;
```
```bash
# exit psql shell
\q
exit
```

For more details
-----------------
[How To Use PostgreSQL with your Django Application](https://www.digitalocean.com/community/tutorials/how-to-use-postgresql-with-your-django-application-on-ubuntu-14-04)