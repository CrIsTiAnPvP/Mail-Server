FROM debian:trixie

################ METADATA #################
LABEL org.opencontainers.image.authors="Cristian Alonso Contreras (CrIsTiiAnPvP)"
LABEL version="1.0"
LABEL description="Docker image for a Dovecot mail server."
LABEL website="cristianac.es"
LABEL org.opencontainers.image.source="https://github.com/CrIsTiAnPvP/Mail-Server"
###########################################

############## INSTALLATION ##############
RUN apt-get update && \
    apt-get install -y dovecot-core dovecot-imapd dovecot-pop3d && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
##########################################

############### CONFIGURE ###############
COPY 10-mail.conf 10-mail.conf 10-auth.conf 10-master.conf 10-ssl.conf /etc/dovecot/conf.d/
RUN useradd -m -u 1001 -s /bin/bash pepe && \
    echo "pepe:password" | chpasswd && \
    useradd -m -u 1002 -s /bin/bash maria && \
    echo "maria:password" | chpasswd
RUN mkdir -p /home/pepe/Maildir /home/maria/Maildir && \
    chown -R pepe:pepe /home/pepe/ && \
    chown -R maria:maria /home/maria/
#########################################

############## PORTS ##############
EXPOSE 143 110
###################################

############## STARTING ##############
CMD ["dovecot", "-F"]
######################################
