FROM ubuntu

RUN apt-get update && apt-get install -y --allow software-properties-common
RUN add-apt-repository ppa:webupd8team/java && apt-get update
RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections
RUN apt-get install -y --allow oracle-java8-installer oracle-java8-set-default

RUN apt-get purge
