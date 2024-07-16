FROM python:3.8.18-bullseye

RUN apt-get update && apt-get install -y --no-install-recommends apt-utils
RUN apt-get upgrade -y
RUN apt-get install -y texlive-full
RUN apt-get install -y xzdec
RUN apt-get install -y wget

RUN tlmgr init-usertree

WORKDIR /app
