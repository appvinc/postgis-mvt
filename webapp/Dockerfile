FROM python:3.6

RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y \
    && apt-get -y install apt-utils libpq-dev python3-dev \
    && apt-get autoremove -y \
    && apt-get clean all

ENV WORKDIR /srv/webapp
RUN mkdir -p $WORKDIR
WORKDIR $WORKDIR
ADD . .
RUN pip install --upgrade pip -r requirements.txt

ENTRYPOINT gunicorn --workers=8 -b 0.0.0.0:8001 app:app
