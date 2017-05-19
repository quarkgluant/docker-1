# vous ajouterez les sources adéquates pour créer un serveur TeamSpeak,
# serveur qui se lancera au démarrage de votre container.
# Celui-ci est considéré comme valide si au moins un utilisateur peut se
# connecter dessus et discuter normalement (pas de configuration hasardeuse),
# donc créez votre Dockerfile avec les options adéquates. Vous devez faire
# en sorte que les sources soient récupérées au build, elles ne doivent pas
# être présentes dans le dépôt..
FROM debian
LABEL maintainer Patrice CADIOT <pathibul.r@gmail.com>

ADD http://dl.4players.de/ts/releases/3.0.13.6/teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 ./

RUN export DEBIAN_FRONTEND=noninteractive \
  && apt-get update \
  && apt-get upgrade -y\
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

# ADD http://dl.4players.de/ts/releases/3.0.13.6/teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 ./
# RUN echo "deb http://debian.proxad.net/debian jessie main" > /etc/apt/sources.list \
#   && echo "deb http://debian.proxad.net/debian jessie-updates main" >> /etc/apt/sources.list \
#   && echo "deb http://security.debian.org jessie/updates main" >> /etc/apt/sources.list \
#   && apt-get update \
#   && apt-get upgrade -y\
#   && apt-get install -y apt-utils bzip2 \
#   && tar xjf teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 \
#   && rm teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 \
#   && mkdir -p /opt \
#   && mv teamspeak3-server_linux_amd64 /opt/teamspeak \
#   && useradd teamspeak \
#   && chown -R teamspeak:teamspeak /opt/teamspeak
# COPY ts3server.ini /opt/teamspeak
# EXPOSE 9987/udp
# EXPOSE 30033
# EXPOSE 10011
# VOLUME ["/opt/teamspeak/data"]
# USER   teamspeak
# WORKDIR /opt/teamspeak
# CMD ./ts3server_minimal_runscript.sh inifile=ts3server.ini start
# docker run  -d --publish=9987:9987/udp --publish=30033:30033/tcp --publish=10011:10011/tcp --name teamspeakprout teamspeak