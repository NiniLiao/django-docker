# ./django-docker/app/Dockerfile
FROM python:3.8.1

# set up the psycopg2
RUN apt-get update && apt-get install -y libpq-dev \
     gcc \
     postgresql-client
RUN pip install psycopg2==2.8.3
RUN apt-get autoremove -y gcc

# set work directory
WORKDIR /opt/app

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install dependencies
RUN pip install --upgrade pip
COPY ./requirements.txt /opt/app/requirements.txt 
RUN chmod +x /opt/app/requirements.txt
RUN pip install -r requirements.txt

# copy project
COPY . /opt/app/
RUN chmod +x /opt/app/docker-entrypoint.sh

ENTRYPOINT [ "/opt/app/docker-entrypoint.sh" ]
