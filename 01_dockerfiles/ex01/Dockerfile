FROM debian
LABEL maintainer Patrice CADIOT <pathibul.r@gmail.com>

ADD http://dl.4players.de/ts/releases/3.0.13.6/teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 ./

RUN export DEBIAN_FRONTEND=noninteractive \
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







# ENV TS_DIRECTORY=/opt/teamspeak

# WORKDIR /

# RUN apt-get update && apt-get install -y bzip2  apt-utils &&\
# 	rm -rf /var/lib/apt/lists/* &&\
# 	tar xjf teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2  &&\
# 	mv teamspeak3-server_linux_amd64 /opt/teamspeak &&\
# 	rm teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 &&\
# 	apt-get purge -y bzip2 &&\
# 	apt-get autoremove -y &&\
# 	mkdir -p ${TS_DIRECTORY}/config ${TS_DIRECTORY}/logs ${TS_DIRECTORY}/bin &&\
# 	mkdir -p ${TS_DIRECTORY}/files ${TS_DIRECTORY}/data &&\
# 	rm -rf /var/lib/apt/lists/*

# RUN groupadd -g 503 teamspeak &&\
# 	useradd -u 503 -g 503 -d ${TS_DIRECTORY} teamspeak &&\
# 	mkdir /data &&\
# 	chown -R teamspeak:teamspeak ${TS_DIRECTORY} &&\
# 	chown -R teamspeak:teamspeak ${TS_DIRECTORY}/config &&\
# 	chown -R teamspeak:teamspeak ${TS_DIRECTORY}/logs &&\
# 	chown -R teamspeak:teamspeak ${TS_DIRECTORY}/bin &&\
# 	chown -R teamspeak:teamspeak ${TS_DIRECTORY}/files &&\
# 	chown -R teamspeak:teamspeak ${TS_DIRECTORY}/data 

# COPY teamspeak ${TS_DIRECTORY}/bin
# COPY ts3server.ini ${TS_DIRECTORY}/config

# EXPOSE 9987/udp
# EXPOSE 30033/udp
# EXPOSE 30033

# EXPOSE 10011/tcp


# WORKDIR ${TS_DIRECTORY}
# RUN cd ${TS_DIRECTORY}

# USER teamspeak

# ENTRYPOINT ["/opt/teamspeak/bin/teamspeak"]
# CMD ["inifile=/opt/teamspeak/config/ts3server.ini"]



# vous ajouterez les sources adéquates pour créer un serveur TeamSpeak,
# serveur qui se lancera au démarrage de votre container.
# Celui-ci est considéré comme valide si au moins un utilisateur peut se
# connecter dessus et discuter normalement (pas de configuration hasardeuse),
# donc créez votre Dockerfile avec les options adéquates. Vous devez faire
# en sorte que les sources soient récupérées au build, elles ne doivent pas
# être présentes dans le dépôt..
# ADD http://dl.4players.de/ts/releases/3.0.13.6/teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 ./
# #COPY ./teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 ./
# RUN echo "deb http://debian.proxad.net/debian jessie main" > /etc/apt/sources.list \
#   && echo "deb http://debian.proxad.net/debian jessie-updates main" >> /etc/apt/sources.list \
#   && echo "deb http://security.debian.org jessie/updates main" >> /etc/apt/sources.list \
#   && apt-get update \
#   && apt-get upgrade \
#   && apt-get install -y apt-utils bzip2 \
#   && tar xjf teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 \
#   && rm teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 \
#   && mkdir -p /opt \
#   && mv teamspeak3-server_linux_amd64 /opt/teamspeak \
#   && useradd teamspeak \
#   && echo "machine_id=" > /opt/teamspeak/ts3server.ini \
#   && echo "default_voice_port=9987" >> /opt/teamspeak/ts3server.ini \
#   && echo "voice_ip=" >> /opt/teamspeak/ts3server.ini \
#   && echo "licensepath=" >> /opt/teamspeak/ts3server.ini \
#   && echo "filetransfer_port=30033" >> /opt/teamspeak/ts3server.ini \
#   && echo "filetransfer_ip=" >> /opt/teamspeak/ts3server.ini \
#   && echo "query_port=10011" >> /opt/teamspeak/ts3server.ini \
#   && echo "query_ip=0.0.0.0, ::" >> /opt/teamspeak/ts3server.ini \
#   && echo "query_ip_whitelist=query_ip_whitelist.txt" >> /opt/teamspeak/ts3server.ini \
#   && echo "query_ip_blacklist=query_ip_blacklist.txt" >> /opt/teamspeak/ts3server.ini \
#   && echo "dbplugin=ts3db_sqlite3" >> /opt/teamspeak/ts3server.ini \
#   && echo "dbpluginparameter=" >> /opt/teamspeak/ts3server.ini \
#   && echo "dbsqlpath=sql/" >> /opt/teamspeak/ts3server.ini \
#   && echo "dbsqlcreatepath=create_sqlite/" >> /opt/teamspeak/ts3server.ini \
#   && echo "dbconnections=10" >> /opt/teamspeak/ts3server.ini \
#   && echo "logpath=logs" >> /opt/teamspeak/ts3server.ini \
#   && echo "logquerycommands=0" >> /opt/teamspeak/ts3server.ini \
#   && echo "dbclientkeepdays=30" >> /opt/teamspeak/ts3server.ini \
#   && echo "logappend=0" >> /opt/teamspeak/ts3server.ini \
#   && echo "query_skipbruteforcecheck=0" >> /opt/teamspeak/ts3server.ini \
#   && chown -R teamspeak:teamspeak /opt/teamspeak
# #serveur qui se lancera au démarrage de votre container
# EXPOSE 9987/udp
# #EXPOSE 9987
# #EXPOSE 30033/udp
# EXPOSE 30033
# EXPOSE 10011
# USER   teamspeak
# WORKDIR /opt/teamspeak
# CMD ./ts3server_minimal_runscript.sh inifile=ts3server.ini start
# #