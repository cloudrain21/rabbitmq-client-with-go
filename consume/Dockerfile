FROM    golang:1.14.1 AS builder
RUN     go get github.com/streadway/amqp
WORKDIR /root/
COPY    consumer.go .
RUN     CGO_ENABLED=0 GOOS=linux go build consumer.go

FROM    alpine:latest  
RUN     apk --no-cache add ca-certificates
WORKDIR /root
COPY    --from=builder /root/consumer .
CMD     ["./consumer"]
