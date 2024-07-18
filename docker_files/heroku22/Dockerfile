FROM heroku/heroku:22-build
ENV PYTHONUNBUFFERED=1

RUN apt-get update
RUN apt-get install -y python3-dev python3-venv python3-pip

RUN /usr/bin/pip3 install wheel pyicu

RUN git clone https://github.com/jessamynsmith/pyicu-wheels.git
WORKDIR /pyicu-wheels
