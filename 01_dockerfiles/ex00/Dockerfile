FROM alpine:latest

# Install needed Packages
RUN apk update && apk add \
	vim

# Run vim 
CMD ["vim"]

# To build the container use
#	docker build . -t vim
# To use the container use
#	docker run -it vim
