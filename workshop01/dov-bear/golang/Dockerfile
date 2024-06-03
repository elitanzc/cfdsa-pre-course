# example of MULTI-STAGE BUILD for app that needs compilation, like golang and java
# first container for compiling and building:
FROM golang:1.22.3-alpine3.20 AS builder

WORKDIR /app

COPY go.mod .
COPY go.sum .
COPY main.go .

# builds executable
RUN go build -o main main.go

# creates a second container for running
FROM alpine:3.20

WORKDIR /app

# copy executable from first container
# no source code here
COPY --from=builder /app/main main
# copy artifacts
COPY public public
COPY templates templates

# install curl for health check
RUN apk update && apk add curl

ENV PORT=3000

EXPOSE ${PORT}

# CMD line must return either 0 (healthy) or 1 (unhealthy)
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
  CMD curl -s http://localhost:${PORT}/healthz || exit 1

# ENTRYPOINT ./main OR
ENTRYPOINT /app/main