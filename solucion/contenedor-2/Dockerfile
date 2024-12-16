# Define la imagen en la que se basa

FROM ubuntu:latest

# Añade metadados
LABEL \
        authors="antlopez" \
        version="1.0" \
        description="Tarea Evaluativa 01 DEAW03, contenedor 2" \
        creationDate="16-12-2024"

# Comandos a ejecutar, incluida la creación del user no-logueable "deaw" radicado en /srv/deaw
RUN \
        apt update \
        && apt -y install nano proftpd openssl proftpd-mod-crypto \
        && useradd deaw -p $(openssl passwd -1 deaw) -m -d /srv/deaw -s /usr/sbin/nologin

# Ficheros a copiar (configuración y recursos)
COPY conf/proftpd.conf /etc/proftpd/
COPY conf/modules.conf /etc/proftpd/
COPY conf/tls.conf /etc/proftpd/
COPY conf/proftpd.key.pem /etc/ssl/private/
COPY conf/proftpd.crt.pem /etc/ssl/certs/
COPY recursos/. /srv/deaw/recursos_2

# Tras la copia aplica los permisos necesarios para "deaw" acceda al directorio "recursos"
RUN \
        chown -R deaw:deaw /srv/deaw

# Informa de los puertos que deberían ser publicados al crear el contenedor
EXPOSE 21 50000-50030