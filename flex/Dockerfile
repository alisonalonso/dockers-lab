FROM alisonalonso/ant
MAINTAINER Alison Alonso <alisonlba@gmail.com>

# Dependencies...
RUN apk update && \
    apk add rsync curl 

# Getting...
ENV FLEX_SDK_DIR=apache-flex-sdk \
    FLEX_VERSION=4.16.0
ENV FLEX_SDK_FILE=${FLEX_SDK_DIR}-${FLEX_VERSION}-bin.tar.gz \
    FLEX_HOME=/opt/${FLEX_SDK_DIR}
ENV PATH=$PATH:$FLEX_HOME/bin

RUN export APACHE_MIRROR=$(curl -s 'http://www.apache.org/dyn/closer.cgi?as_json=1' | \
    grep "preferred" | cut -d ':' -f3 | cut -d'"' -f1 | awk -F// '{print $NF}' | sed 's/.$//') && \
    curl -o /${FLEX_SDK_FILE} http://${APACHE_MIRROR}/flex/${FLEX_VERSION}/binaries/${FLEX_SDK_FILE}

# Extracting...
RUN tar -xzf ${FLEX_SDK_FILE} && \
    mv ${FLEX_SDK_DIR}-${FLEX_VERSION}-bin /opt/${FLEX_SDK_DIR}

# Installing...
#RUN cd /opt/${FLEX_SDK_DIR} && \
#    ant -f installer.xml -Dinput.air.download=y -Dinput.flash.download=y -Dinput.fontswf.download=y && \
#    rm -rf /${FLEX_SDK_FILE} /var/cache/apk/*

WORKDIR /src
