FROM debian:bookworm-slim
RUN sed -i 's|deb.debian.org/debian/|blademaster.home:8081/repository/|g' /etc/apt/sources.list.d/*
RUN apt -y update
RUN apt -y install build-essential git cmake libcrypto++-dev pkg-config
RUN apt -y install flex bison yacc autoconf automake
RUN git clone https://github.com/willamowius/ptlib.git
RUN cd ptlib && ./configure && make -j16 && make install
RUN git clone https://github.com/willamowius/h323plus.git
RUN cd h323plus && ./configure --enable-h235 && make -j16 && make install
RUN git clone https://github.com/willamowius/gnugk.git
RUN cd gnugk && ./configure --enable-h46018 --enable-avaya && make -j16 && make install
RUN cd gnugk && make addpasswd 
ENV LD_LIBRARY_PATH=/usr/local/lib
COPY gatekeeper.ini /etc

ENTRYPOINT [ "/usr/bin/gnugk", "-c", "/etc/gatekeeper.ini", "-ttttttttt", "-rr"]
