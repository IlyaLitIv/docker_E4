FROM python:3.11-alpine AS base

# create and set the working directory inside container
ENV HOME=/home/app
ENV APP_HOME=/home/app/web
RUN mkdir -p $APP_HOME
RUN mkdir $APP_HOME/static
WORKDIR $APP_HOME

# pip upgrade and install requirements
COPY requirements.txt $APP_HOME
RUN pip install --upgrade pip
RUN pip install -r requirements.txt

# copy current folder to the container
COPY . $APP_HOME

RUN python manage.py makemigrations
# RUN python manage.py migrate
# RUN python manage.py createsuperuser
RUN python manage.py collectstatic --noinput
# CMD ["gunicorn", "DeployProject.wsgi:application", "-b", "0.0.0.0:8000"]