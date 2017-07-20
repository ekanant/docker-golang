# This is golang
# VERSION 1
# Author: Ekanant

FROM golang:1.8.3

MAINTAINER Ekanant ekanant2535@gmail.com

# install require software
RUN apt-get update && apt-get install -y --no-install-recommends build-essential unzip nano pkg-config libaio1

RUN mkdir -p /usr/lib/oracle/12.1/client64/lib && mkdir -p /usr/include/oracle/12.1/client64/

ENV LD_LIBRARY_PATH /usr/lib:/usr/local/lib:/usr/lib/oracle/12.1/client64/lib
ENV NLS_LANG THAI_THAILAND.TH8TISASCII

COPY instantclient-basic-linux.x64-12.1.0.2.0.zip /tmp/
COPY instantclient-sdk-linux.x64-12.1.0.2.0.zip /tmp/
COPY oci8.pc /usr/lib/pkgconfig/

RUN cd /tmp && unzip instantclient-basic-linux.x64-12.1.0.2.0.zip 
RUN cp /tmp/instantclient_12_1/* /usr/lib/oracle/12.1/client64/lib/

RUN cd /tmp && unzip instantclient-sdk-linux.x64-12.1.0.2.0.zip
RUN cp /tmp/instantclient_12_1/sdk/include/* /usr/include/oracle/12.1/client64/ 

RUN ln -s /usr/lib/oracle/12.1/client64/lib/libclntsh.so.12.1 /usr/lib/oracle/12.1/client64/lib/libclntsh.so
RUN ln -s /usr/lib/oracle/12.1/client64/lib/libocci.so.12.1 /usr/lib/oracle/12.1/client64/lib/libocci.so

RUN go get github.com/mattn/go-oci8

RUN rm -rf /tmp/*