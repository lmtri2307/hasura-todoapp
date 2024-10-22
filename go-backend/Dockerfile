FROM golang:1.23-alpine3.20 as builder
WORKDIR /build
COPY . .
RUN go mod download
RUN go build -o ./binary

FROM gcr.io/distroless/base-debian12
WORKDIR /app
COPY --from=builder /build/binary ./binary
CMD [ "/app/binary" ]
