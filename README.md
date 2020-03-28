# NPORT-P Python Scraper + API

## Setup

### Install:

- Python 3.8.1 https://www.python.org/downloads/release/python-381/
- pip https://pip.pypa.io/en/stable/installing/
- PostgreSQL 10.12 https://www.enterprisedb.com/downloads/postgres-postgresql-downloads
- pgAdmin4 https://www.postgresql.org/ftp/pgadmin/pgadmin4/v4.19/windows/

### Setup PostgreSQL

1. Launch pgAdmin4, navigate to the browser based UI (for me it was http://127.0.0.1:19217/browser/) 
2. Connect to your local PostgreSQL server and create a new Login/User called `dev` with password `password`
3. Create a Database called `NPS`, and set the owner to be the `dev` account you just created

### Install Required Packages/Libraries

- Run: `pip install -r requirements.txt` in the root of the project 

## Python Scraper 

### Running

*Note: You will need to have the database setup by running `python manage.py migrate` from the api folder.*

From the python_scraper folder run: `scrapy crawl sec_nport_p`

### Config Options

In `python_scraper/python_scraper/settings.py` you can adjust how fast the spider requests pages and other spider
settings.

## API

### Running

Currently uses the Postgres database setup earlier. 

Make sure you have a `dbsettings.json` file created in the root api folder (right next to `manage.py`) with the following contents: 

```
{
    "DB_NAME": "NPS",
    "DB_USER": "dev",
    "DB_PASSWORD": "password",
    "DB_HOST": "localhost",
    "DB_PORT": "5432"
}
```

From the api folder:

```
python manage.py migrate
python manage.py runserver
```

Server is now running on `localhost:8000`, there is readable docs generated there.
