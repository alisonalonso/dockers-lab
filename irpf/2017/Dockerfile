FROM alisonalonso/java:jre8
MAINTAINER Alison Alonso <alisonlba@gmail.com>

# Dependencies
RUN apk update && apk add \
    libgcc \
    libxext \
    libxrender \
    libxtst \
    musl \
    xorg-server

ENV LD_LIBRARY_PATH /usr/lib:/lib:/lib64

# Getting IRPF2017 program 
ADD http://downloadirpf.receita.fazenda.gov.br/irpf/2017/irpf/arquivos/IRPF2017-1.1.zip \
    /

# Extracting zip file
RUN unzip -d /opt IRPF2017-1.1.zip && \
    rm -rf IRPF2017-1.1.zip 

ENTRYPOINT ["java", "-jar"]
CMD ["/opt/IRPF2017/irpf.jar"]
