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

# Getting both IRPF2016 and Receitanet program 
ADD http://downloadirpf.receita.fazenda.gov.br/irpf/2016/IRPF2016-1.2.zip \
    http://downloadirpf.receita.fazenda.gov.br/receitanet/Receitanet-1.07.jar \
    /

# Extracting zip file
RUN unzip -d /opt IRPF2016-1.2.zip && \
    echo "INSTALL_PATH=/opt/receitanet" | tee args.properties && \
    java -jar Receitanet-1.07.jar -options args.properties && \
    ln -sf /opt/receitanet/receitanet.jar /receitanet && \
    rm -rf IRPF2016-1.2.zip Receitanet-1.07.jar args.properties

ENTRYPOINT ["java", "-jar"]
CMD ["/opt/IRPF2016/irpf.jar"]