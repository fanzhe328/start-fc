FROM golang:1.12.16-stretch
RUN mkdir -p $GOPATH/src/golang.org/x/
RUN cd $GOPATH/src/golang.org/x/ && git clone https://github.com/golang/net.git
RUN cd $GOPATH/src/golang.org/x/ &&  git clone https://github.com/golang/sys.git
RUN go get github.com/awesome-fc/golang-runtime
RUN go get github.com/gorilla/websocket

WORKDIR /tmp
COPY . .

RUN go build -o bootstrap main.go
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
RUN cp /tmp/bootstrap  ./bootstrap
ENTRYPOINT ["/usr/src/app/bootstrap"]