#
# Docker file for Intan RHD2000 Interface CI
#
FROM debian:buster

# prepare
RUN apt-get update -qq
RUN apt-get install -yq eatmydata

# install build essentials
RUN eatmydata apt-get install -yq gcc g++ clang

# install build dependencies
RUN eatmydata apt-get install -yq --no-install-recommends \
    build-essential \
    dpkg-dev \
    devscripts \
    debhelper \
    debspawn \
    cmake \
    qt5-default \
    qtmultimedia5-dev

# finish
RUN mkdir /build
WORKDIR /build
