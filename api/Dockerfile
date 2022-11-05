#pulls official base image
FROM python:3.8

#Running Environment setup
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1
COPY . /app
WORKDIR /app

#Depencies set-up
RUN pip3 install -r requirements.txt
RUN python manage.py makemigrations
RUN python manage.py migrate

EXPOSE 8000

#Runs Server
CMD gunicorn -b 0.0.0.0:8000 --worker-class=gevent --worker-connections=1000 --workers=5 backend.wsgi
