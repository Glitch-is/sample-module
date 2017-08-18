FROM python:latest

ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8

RUN pip3 install flask
RUN apt-get update -yqq && apt-get install -yqq iputils-ping
RUN useradd adversary --shell /bin/bash --no-create-home
ADD . /app
WORKDIR /app
RUN chown root:adversary /app && chmod 755 /app

ENV FLASK_APP=app.py
EXPOSE 5000
USER adversary
CMD ["flask", "run", "-h", "0.0.0.0"]
