  ########################
#######  Dockerfile  #######
##                        ##
##   Bitcoin Node Image   ##
##   ==================   ##
##                        ##
##   Version: 251208.01   ##
##                        ##
##  Core/Knots by Rui P.  ##
##                        ##
############################
  ########################


# Get the latest Debian base image
FROM debian:latest

# Set '/home' as working directory to install the Bitcoin Core
WORKDIR /home

# Copy compressed Bitcoin Node (core/knots) file to working directory
COPY bitcoin*.tar.gz .

# Run commands during build
RUN tar xzf bitcoin*tar.gz \
	# Decompress Bitcoin Node file and cleanup
	&& rm *.tar.gz \
	# Name app folder as 'bitcoin-node'
	&& mv bitcoin* bitcoin-node \
	# Create blockchain data directory
	&& mkdir bitcoin-node-data \
	# Update package sources and upgrade OS
	&& apt-get update && apt-get full-upgrade -y

# On container start launch the Bitcoin Node
ENTRYPOINT ["./bitcoin-node/bin/bitcoind","-datadir=/home/bitcoin-node-data"]
