FROM nmaas87/docker-raspbian_xinit:fixed
MAINTAINER Nico Maas <mail@nico-maas.de>
ENV DEBIAN_FRONTEND noninteractive
RUN [ "cross-build-start" ]

RUN apt-get update \
    && apt-get install -yq --no-install-recommends \
        git-core python3-pip python3-pyqt5 python3-gi python3-setuptools gir1.2-webkit-3.0=2.4.9-1~deb8u1+rpi1 gir1.2-javascriptcoregtk-3.0=2.4.9-1~deb8u1+rpi1 libjavascriptcoregtk-3.0-0=2.4.9-1~deb8u1+rpi1 libwebkitgtk-3.0-0=2.4.9-1~deb8u1+rpi1 \
    && apt-get autoremove -qqy \
    && apt-get autoclean -y \
    && apt-get clean && rm -rf /var/lib/apt/lists/* && mkdir /var/lib/apt/lists/partial \
    && pip3 install Flask \
    && pip3 install git+https://github.com/r0x0r/pywebview.git@eval-js \
    && mkdir /usr/src/app/templates /usr/src/app/static

# copy program
COPY src /usr/src/app

# start init system
ENV INITSYSTEM on

RUN [ "cross-build-end" ]  
