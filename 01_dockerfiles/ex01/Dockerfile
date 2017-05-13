FROM debian
LABEL maintainer Patrice CADIOT <pathibul.r@gmail.com>

ADD http://dl.4players.de/ts/releases/3.0.13.6/teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 ./

RUN export DEBIAN_FRONTEND=noninteractive \
  && echo "deb http://debian.proxad.net/debian jessie main" > /etc/apt/sources.list \
  && echo "deb http://debian.proxad.net/debian jessie-updates main" >> /etc/apt/sources.list \
  && echo "deb http://security.debian.org jessie/updates main" >> /etc/apt/sources.list \
  && apt-get update \
  && apt-get upgrade \
  && apt-get install -y apt-utils bzip2 \
  && tar xjf teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 \
  && rm teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 \
  && mv teamspeak3-server_linux_amd64 /opt/teamspeak

RUN useradd teamspeak && mkdir -p /opt/teamspeak/data && chown teamspeak:teamspeak /opt/teamspeak/data
VOLUME ["/opt/teamspeak/data"]

EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 10011
WORKDIR /opt/teamspeak
USER teamspeak

#serveur qui se lancera au démarrage de votre container
CMD /opt/teamspeak/ts3server_minimal_runscript.sh start
