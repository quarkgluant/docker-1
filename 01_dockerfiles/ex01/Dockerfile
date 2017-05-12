FROM debian
MAINTAINER Patrice CADIOT <pathibul.r@gmail.com>

ADD http://dl.4players.de/ts/releases/3.0.13.6/teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 ./

RUN apt-get update && apt-get install -y bzip2 &&\
	tar xjf ./teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 &&\
    mv teamspeak3-server_linux_amd64 /opt/teamspeak &&\
    rm teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2

RUN    useradd teamspeak && mkdir /opt/teamspeak/data && chown teamspeak:teamspeak /opt/teamspeak/data
VOLUME ["/opt/teamspeak/data"]
USER   teamspeak

EXPOSE 9987/udp 30033 10011

ENTRYPOINT ["/opt/teamspeak/ts3server_startscript.sh"]
CMD ["start"]
