# shopbikes


## Development setup

We use [Virtualenv](https://virtualenv.pypa.io/en/stable/) to manage different Python (make sure it's python3) environments.

Retrieve our project
```
$ git clone https://github.com/wujunhua/shopbikes
$ cd shopbikes
```

Install dependencies in your environment
```
$ pip install -r requirements.txt
```

Install Postgres locally. Make sure to set the `$PATH` variable as described in the instructions.
Connect to Postgres via the command line to create a database and user

For Mac
```
$ psql postgres
$ CREATE DATABASE shopbikes;
$ CREATE USER shopbikes WITH PASSWORD 'yourpassword';
$ GRANT ALL PRIVILEGES ON DATABASE shopbikes TO shopbikes;
$ ALTER USER shopbikes WITH SUPERUER;
```

For Windows (You will enter your postgres password in the Postgres installation)
```
$ psql -U postgres
$ CREATE DATABASE shopbikes;
$ CREATE USER shopbikes WITH PASSWORD 'yourpassword';
$ ALTER DATABASE shopbikes OWNER TO shopbikes;
$ ALTER USER shopbikes WITH SUPERUER;
```

We will store passwords and sensitive information in our `main/settings.py` file.
Because of this, we do not want to check in our settings.py file into git.
We use a template for the settings file, `/main/sample_settings.py`. Copy this file
to `/main/settings.py` and change the database info to match your database name, user, and password.

Make and run [migrations](https://docs.djangoproject.com/en/1.10/topics/migrations/)
```
$ python manage.py makemigrations
$ python manage.py migrate
```

Create Django superuser so you can access the admin portal
```
$ python manage.py createsuperuser
```

Start server
```
$ python manage.py runserver
```
