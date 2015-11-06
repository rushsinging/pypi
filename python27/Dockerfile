FROM ubuntu:14.04

ENV LANG C.UTF-8

RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

RUN rm /bin/sh && ln -s /bin/bash /bin/sh

RUN apt-get -y update &&  apt-get -y install python2.7-dev & apt-get -y install python-setuptools && easy_install pip && pip install virtualenv virtualenvwrapper 
