FROM debian:latest

# Install needed packages
RUN apt-get update && apt-get install -y \
	curl \
	bzip2

# Add user for teamspeak server
RUN useradd ts
WORKDIR /home/ts

# Create and config teamspeak server
RUN curl http://dl.4players.de/ts/releases/3.0.13.6/teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 > teamspeak-server.tar.bz2 
RUN tar -xjvf teamspeak-server.tar.bz2
RUN rm -rf teamspeak-server.tar.bz2
WORKDIR teamspeak3-server_linux_amd64

# Ports
EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 10011

# Run teamspeak server
USER ts
ENTRYPOINT ["sh", "./ts3server_minimal_runscript.sh", "createinifile=1"]

# To build the container use:
#	docker build . -t ts
# To run the container use: 
#	docker run -p 9987:9987/udp -p 30033:30033 -p 10011:10011 ts
