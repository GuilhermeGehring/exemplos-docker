FROM golang:rc-alpine3.14 AS builder

WORKDIR /go/src/app
COPY . .

RUN go env -w GO111MODULE=off
RUN go get -d -v ./...
RUN go install -v ./...
RUN go build main.go

FROM scratch
WORKDIR /go/src/app
COPY --from=builder /go/src/app/main .

CMD ["./main"]