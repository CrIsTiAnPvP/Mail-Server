FROM debian:trixie

################ METADATA #################
LABEL org.opencontainers.image.authors="Cristian Alonso Contreras (CrIsTiiAnPvP)"
LABEL version="1.0"
LABEL description="Docker image for a BIND9 Dns server."
LABEL website="cristianac.es"
LABEL org.opencontainers.image.source="https://github.com/CrIsTiAnPvP/Mail-Server"
###########################################

############## INSTALLATION #################
RUN apt-get update && \
	apt-get install -y bind9 bind9utils bind9-doc dnsutils && \
	apt-get clean && \
	rm -rf /var/lib/apt/lists/*
###########################################

############### CONFIGURE ###################
COPY named.conf.options /etc/bind/named.conf.options
COPY named.conf.local /etc/bind/named.conf.local
COPY db.isrv.test /etc/bind/zones/db.isrv.test
###########################################

############## STARTING ####################
CMD ["named", "-g", "-c", "/etc/bind/named.conf"]
###########################################

############## VOLUMES ####################
VOLUME ["/etc/bind/zones"]
###########################################