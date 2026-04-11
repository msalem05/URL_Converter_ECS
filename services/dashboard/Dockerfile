# golang:1.23-alpine Base Image
FROM golang@sha256:383395b794dffa5b53012a212365d40c8e37109a626ca30d6151c8348d380b5f AS builder

WORKDIR /app

COPY go.* ./

RUN go mod download 

COPY . .

RUN CGO_ENABLED=0 go build -o /app/dashboard .

FROM gcr.io/distroless/static-debian12@sha256:20bc6c0bc4d625a22a8fde3e55f6515709b32055ef8fb9cfbddaa06d1760f838

COPY --from=builder /app/dashboard /dashboard

WORKDIR /app

USER nonroot

EXPOSE 8081

CMD ["/dashboard"]