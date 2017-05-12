FROM golang
LABEL maintainer Patrice CADIOT <pathibul.r@gmail.com>
SHELL ["/bin/bash", "-c"]
RUN apt-get update && apt-get install -y libpam0g-dev &&\
	echo 'export GOPATH' >> $HOME/.bashrc &&\
	echo 'export PATH=$PATH:$GOPATH/bin' >> $HOME/.bashrc &&\
	source $HOME/.bashrc &&\
	mkdir -p $GOPATH/src/github.com/gogits &&\
	cd $GOPATH/src/github.com/gogits &&\
	git clone --depth=1 -b develop https://github.com/gogits/gogs.git &&\
	cd gogs && go get ./... && go build 
WORKDIR /go/src/github.com/gogits/gogs
EXPOSE 3000
CMD ./gogs web