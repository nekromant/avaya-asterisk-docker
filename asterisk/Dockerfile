FROM debian:bullseye
RUN echo sd
RUN sed -i 's|deb.debian.org/debian/|blademaster.home:8081/repository/|g' /etc/apt/sources.list
RUN sed -i "s|main|main contrib non-free non-free-firmware|g" /etc/apt/sources.list
RUN apt update 

RUN apt -y install asterisk-ooh323 asterisk
COPY ooh323.conf /etc/asterisk/
COPY extensions.ael /etc/asterisk/
ENTRYPOINT /usr/sbin/asterisk -vvf