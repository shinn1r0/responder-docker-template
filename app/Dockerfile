FROM python:latest
LABEL maintainer="shinichir0 <github@shinichironaito.com>"

ENV DEBIAN_FRONTEND noninteractive
ENV LC_ALL C.UTF-8
ENV LANG C.UTF-8
ENV HOME /root

RUN apt-get update && apt-get upgrade -y && apt-get autoremove -y && apt-get autoclean -y

RUN pip install --upgrade pip setuptools pipenv

COPY Pipfile ./
COPY Pipfile.lock ./

RUN set -ex && pipenv install --deploy --system

RUN apt-get install curl unzip -y
RUN mkdir -p /usr/share/fonts/opentype/noto
RUN curl -O https://noto-website-2.storage.googleapis.com/pkgs/NotoSansCJKjp-hinted.zip
RUN unzip NotoSansCJKjp-hinted.zip -d /usr/share/fonts/opentype/noto
RUN rm NotoSansCJKjp-hinted.zip
RUN apt-get install fontconfig
RUN fc-cache -f

WORKDIR /root
