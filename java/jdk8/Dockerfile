# AlpineLinux with a glibc-2.21 and Oracle Java 8
FROM alpine:3.3

MAINTAINER Alison Alonso <alisonlba@gmail.com>

##
# Glibc
##
ENV GLIBC_VERSION 2.23-r1

#    https://github.com/andyshinn/alpine-pkg-glibc/releases/download/2.23-r1/glibc-bin-2.23-r1.apk
ADD https://github.com/andyshinn/alpine-pkg-glibc/releases/download/2.23-r1/glibc-${GLIBC_VERSION}.apk /glibc-apk/glibc.apk
RUN apk add --allow-untrusted /glibc-apk/glibc.apk

#
#RUN /usr/glibc/usr/bin/ldconfig /lib /usr/glibc/usr/lib && \
#    echo 'hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4' >> /etc/nsswitch.conf
#

##
# Java
##

# Java Version and other ENV
ENV JAVA_VERSION_MAJOR=8 \
    JAVA_VERSION_MINOR=92 \
    JAVA_VERSION_BUILD=14 \
    JAVA_PACKAGE=jdk \
    JAVA_HOME=/opt/jdk \
    PATH=${PATH}:/opt/jdk/bin \
    LANG=C.UTF-8


# do all in one step
RUN apk upgrade --update && \
    apk add --update curl ca-certificates bash && \
    mkdir /opt && curl -jksSLH "Cookie: oraclelicense=accept-securebackup-cookie" -o /tmp/java.tar.gz \
    http://download.oracle.com/otn-pub/java/jdk/${JAVA_VERSION_MAJOR}u${JAVA_VERSION_MINOR}-b${JAVA_VERSION_BUILD}/${JAVA_PACKAGE}-${JAVA_VERSION_MAJOR}u${JAVA_VERSION_MINOR}-linux-x64.tar.gz && \
    gunzip /tmp/java.tar.gz && \
    tar -C /opt -xf /tmp/java.tar && \
    apk del curl && \
    ln -s /opt/jdk1.${JAVA_VERSION_MAJOR}.0_${JAVA_VERSION_MINOR} /opt/jdk && \
    rm -rf /tmp/* /var/cache/apk/*

# EOF
