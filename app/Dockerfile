FROM python:3.7-alpine

LABEL MAINTAINER="Andreas Ehrlund <a.ehrlund@gmail.com>"

WORKDIR /var/www

RUN pip install -r requirements.txt

EXPOSE 5000

# Keeps Python from generating .pyc files in the container
#ENV PYTHONDONTWRITEBYTECODE 1

# Turns off buffering for easier container logging
#ENV PYTHONUNBUFFERED 1

ADD . /var/www/
RUN addgroup www
RUN adduser -D -G www www -s /bin/sh
USER www

CMD [ "gunicorn", "-w", "4", "--bind", "0.0.0.0:5000", "wsgi"]