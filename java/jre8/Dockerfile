# AlpineLinux with a glibc-2.21 and Oracle Java 8
FROM alpine:3.3

MAINTAINER Alison Alonso <alisonlba@gmail.com>

##
# Glibc
##
ENV GLIBC_VERSION 2.23-r1

#    https://github.com/andyshinn/alpine-pkg-glibc/releases/download/2.23-r1/glibc-bin-2.23-r1.apk
ADD https://github.com/andyshinn/alpine-pkg-glibc/releases/download/2.23-r1/glibc-${GLIBC_VERSION}.apk /tmp/glibc.apk
RUN apk add --allow-untrusted /tmp/glibc.apk

#
#RUN /usr/glibc/usr/bin/ldconfig /lib /usr/glibc/usr/lib && \
#    echo 'hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4' >> /etc/nsswitch.conf
#

##
# Java
##

# Java Version and other ENV
ENV LANG=C.UTF-8 \
    JAVA_VERSION_MAJOR=8 \
    JAVA_VERSION_MINOR=91 \
    JAVA_VERSION_BUILD=14 \
    JAVA_PACKAGE=jre

ENV JAVA_HOME=/opt/${JAVA_PACKAGE} \
    PATH=${PATH}:/opt/${JAVA_PACKAGE}/bin


ADD http://javadl.oracle.com/webapps/download/AutoDL?BundleId=207765 /tmp/java.tar.gz

# do all in one step
RUN apk upgrade --update && \
    apk add --update bash && \
    mkdir /opt && tar -C /opt -xzvf /tmp/java.tar.gz && \
    ln -s /opt/${JAVA_PACKAGE}1.${JAVA_VERSION_MAJOR}.0_${JAVA_VERSION_MINOR} /opt/${JAVA_PACKAGE} && \
    rm -rf /tmp/* /var/cache/apk/*

# EOF
