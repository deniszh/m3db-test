FROM golang:1.14-alpine3.12 as builder
RUN apk --no-cache add git
WORKDIR /root
RUN go get github.com/gorsuch/haggar
RUN go build github.com/gorsuch/haggar

FROM alpine:3.12
RUN apk --no-cache add curl
WORKDIR /root/
COPY --from=builder /root/haggar .
CMD ["./haggar", "-agents=100", "-metrics=10000", "-carbon='127.0.0.1:2003'"]
