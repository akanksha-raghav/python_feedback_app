## Python Heroku Deployment
Steps to create a postgres database and deply a Python app to Heroku

### Install guinicorn locally
pipenv install gunicorn<br>
or<br>
pip install gunicorn<br>
### Install Heroku CLI
https://devcenter.heroku.com/articles/heroku-cli

### Login via CLI
heroku login
### Create app
heroku create appname
### Create database
heroku addons:create heroku-postgresql:hobby-dev --app appname
### Get URI
heroku config --app appname

# Add to your app
Create Procfile
touch Procfile

# Add this
web: gunicorn app:app
### Create requirements.txt
pip freeze > requirements.txt
### Create runtime.txt
touch runtime.txt

# Add this
python-3.7.2

### Deploy with Git
git init<br>
git add . && git commit -m 'Deploy'<br>
heroku git:remote -a appname<br>
git push heroku master<br>
### Add table to remote database
heroku run python<br>
>>> from app import db<br>
>>> db.create_all()<br>
>>>exit()<br>
### Visit app
heroku open
