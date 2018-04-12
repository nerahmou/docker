FROM debian

ENV TS3SERVER_LICENSE=accept

RUN apt-get update && apt-get upgrade -y
RUN	apt-get install curl -y
RUN apt-get install bzip2 -y

EXPOSE 9987/udp
EXPOSE 10011
EXPOSE 30033

RUN useradd ness
WORKDIR /home/ts3

RUN curl http://dl.4players.de/ts/releases/3.1.1/teamspeak3-server_linux_amd64-3.1.1.tar.bz2 > ts3-server.tar.bz2
RUN tar -xjvf ts3-server.tar.bz2
RUN rm ts3-server.tar.bz2

WORKDIR teamspeak3-server_linux_amd64
ADD ts3server.ini ./

USER ness
ENTRYPOINT sh ts3server_minimal_runscript.sh inifile=ts3server.ini
