# Define la imagen en la que se basa

FROM ubuntu:latest

# Añade metadados
LABEL \
        authors="antlopez" \
        version="1.0" \
        description="Tarea Evaluativa 01 DEAW03, contenedor 1" \
        creationDate="15-12-2024"

# Comandos a ejecutar, incluida la eliminación de welcome.msg para que no moleste
RUN \
        apt update \
        && apt -y install nano proftpd \
        && rm /srv/ftp/welcome.msg

# Ficheros a copiar (configuración y recursos)
COPY conf/proftpd.conf /etc/proftpd/
COPY recursos/. /srv/ftp/recursos_1

# Tras la copia aplica el cambio de propietario para que "ftp" acceda a "recursos_1"
RUN \
       chown -R ftp:nogroup /srv/ftp

# Informa de los puertos que deberían ser publicados al crear el contenedor
EXPOSE 21 50000-50030
