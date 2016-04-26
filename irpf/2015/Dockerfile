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

# Getting both IRPF2015 and Receitanet program 
ADD http://www28.receita.fazenda.gov.br/publico/programas/IRPF/2015/PGDIRPF2015/Java/zip/IRPF2015-1.3.zip \
    /

# Extracting zip file
RUN unzip -d /opt IRPF2015-1.3.zip && \
    rm -rf IRPF2015-1.3.zip

ENTRYPOINT ["java", "-jar"]
CMD ["/opt/IRPF2015/irpf.jar"]