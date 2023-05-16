FROM golang:alpine AS builder

ENV CGO_ENABLED 0

ENV GOOS linux

WORKDIR /build

ADD go.mod .

COPY . .

RUN go build -o hello hello.go

FROM alpine

RUN apk update --no-cache && apk add --no-cache ca-certificates

WORKDIR /build

COPY --from=builder /build/hello /build/hello

CMD ["/build/hello"]
