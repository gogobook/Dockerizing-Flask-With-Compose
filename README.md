## Dockerizing pgAdmin4 With Compose

Featuring:

- Docker v17.03.1-ce
- Docker Compose v1.12.0
- pgAdmin4 v1.4

Origin code from blow blog.  
**Check out the awesome blog post here > https://realpython.com/blog/python/dockerizing-flask-with-compose-and-machine-from-localhost-to-the-cloud/**

## pgAdmin served by gunicorn and nginx
web source code came from web in pgAdmin4  
pgAdmin4.wsgi rename to wsgi.py for gunicorn  
requirements.txt update.  
You need to setup your config_local.py and volumes in docker-compose.yml

## Create Database Migrations
(Came from pgAdmin4 manual)

In order to make changes to the SQLite DB, navigate to the 'web' directory:

`(pgadmin4) $ cd $PGADMIN4_SRC/web`

Create a migration file with the following command:

`(pgadmin4) $ FLASK_APP=pgAdmin4.py flask db revision`

This will create a file in: $PGADMIN4_SRC/web/migrations/versions/ .
Add any changes to the 'upgrade' function.

There is no need to increment the SETTINGS_SCHEMA_VERSION.

## Connect to PostgreSQL Database

PostgreSQL Database is at 0.0.0.0:5432, setup by docker-compose.  
pgAdmin4 can connect it by your ip:5432.

## SSL may need to setup.

## Note
If you want to use newest pgAdmin4 from https://github.com/postgres/pgadmin4.  
You need add `Flask-Migrate==2.0.3` to requirements.txt or you will get error `ImportError: No module named 'flask_migrate'`.