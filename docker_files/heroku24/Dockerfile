FROM heroku/heroku:24-build
ENV PYTHONUNBUFFERED=1
USER root
RUN apt-get update
RUN apt-get install -y python3-dev python3-venv python3-pip python3-full

RUN python3 -m venv pyicu-venv
RUN pyicu-venv/bin/pip install wheel pyicu

RUN git clone https://github.com/jessamynsmith/pyicu-wheels.git
WORKDIR /pyicu-wheels
