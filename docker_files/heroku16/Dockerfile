FROM heroku/heroku:16-build
ENV PYTHONUNBUFFERED 1

RUN apt-get update
RUN apt-get install -y software-properties-common
RUN add-apt-repository ppa:jonathonf/python-3.6
RUN apt-get update
RUN apt-get install -y python3.6 python3.6-dev python3.6-venv python3-pip

RUN /usr/bin/pip3 install wheel pyicu

RUN git clone https://github.com/jessamynsmith/pyicu-wheels.git
WORKDIR /pyicu-wheels
