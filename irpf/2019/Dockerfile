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

# Getting IRPF2019 program 
ADD http://downloadirpf.receita.fazenda.gov.br/irpf/2019/irpf/arquivos/IRPF2019-1.5.zip \
    /

# Extracting zip file
RUN unzip -d /opt IRPF2019-1.5.zip && \
    rm -rf IRPF2019-1.5.zip 

ENTRYPOINT ["java", "-jar"]
CMD ["/opt/IRPF2019/irpf.jar"]
