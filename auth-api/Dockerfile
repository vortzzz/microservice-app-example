# Build stage
FROM golang:1.18 AS build
WORKDIR /app
COPY . .
RUN go mod init github.com/bortizf/microservice-app-example/tree/master/auth-api || true \
    && go mod tidy \
    && CGO_ENABLED=0 GOOS=linux go build -o auth-api .

# Run stage (static binary; no apk needed)
FROM debian:bookworm-slim
WORKDIR /app
COPY --from=build /app/auth-api .
EXPOSE 8000
CMD ["./auth-api"]
