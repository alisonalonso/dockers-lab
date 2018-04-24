##
# Alpine Linux with a glibc-2.23 and Oracle Java 8 - JDK
#
FROM alpine:3.6

MAINTAINER Alison Alonso <alisonlba@gmail.com>

##
# Glibc
# @see https://github.com/andyshinn/alpine-pkg-glibc
#
ENV GLIBC_VERSION 2.25-r0

# ADD https://github.com/sgerrand/alpine-pkg-glibc/releases/download/${GLIBC_VERSION}/glibc-${GLIBC_VERSION}.apk /tmp/glibc.apk
RUN apk upgrade --update && \
    apk add --update curl ca-certificates bash && \
    curl -L -o /tmp/glibc.apk https://github.com/sgerrand/alpine-pkg-glibc/releases/download/${GLIBC_VERSION}/glibc-${GLIBC_VERSION}.apk && \
    apk add --allow-untrusted /tmp/glibc.apk

##
# JDK8
#

# Java Version and other ENV
ENV JAVA_VERSION_MAJOR=8 \
    JAVA_VERSION_MINOR=144 \
    JAVA_VERSION_BUILD=01 \
    JAVA_PACKAGE=jdk \
    JAVA_HOME=/opt/jdk \
    PATH=${PATH}:/opt/jdk/bin \
    LANG=C.UTF-8

RUN mkdir /opt && curl -jkLH "Cookie: oraclelicense=accept-securebackup-cookie" -o /tmp/java.tar.gz \
    http://download.oracle.com/otn-pub/java/jdk/${JAVA_VERSION_MAJOR}u${JAVA_VERSION_MINOR}-b${JAVA_VERSION_BUILD}/090f390dda5b47b9b721c7dfaa008135/${JAVA_PACKAGE}-${JAVA_VERSION_MAJOR}u${JAVA_VERSION_MINOR}-linux-x64.tar.gz && \
    tar -C /opt -xzf /tmp/java.tar.gz && \
    apk del curl && \
    ln -s /opt/jdk1.${JAVA_VERSION_MAJOR}.0_${JAVA_VERSION_MINOR} /opt/jdk && \
    rm -rf /tmp/* /var/cache/apk/*
