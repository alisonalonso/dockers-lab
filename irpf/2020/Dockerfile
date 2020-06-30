FROM alisonalonso/java:jre8
MAINTAINER Alison Alonso <alisonlba@gmail.com>

# Dependencies
RUN apk update && apk add \
    libgcc \
    libxext \
    libxrender \
    libxtst \
    musl \
    libxi \
    xorg-server

ENV LD_LIBRARY_PATH /usr/lib:/lib:/lib64

# Getting IRPF2020 program 
ADD http://downloadirpf.receita.fazenda.gov.br/irpf/2020/irpf/arquivos/IRPF2020-1.9.zip \
    /

# Extracting zip file
RUN unzip -d /opt IRPF2020-1.9.zip && \
    rm -rf IRPF2020-1.9.zip 

ENTRYPOINT ["java", "-jar"]
CMD ["/opt/IRPF2020/irpf.jar"]
