FROM golang:1.23

WORKDIR /app

COPY go.* ./

RUN go mod download 

COPY . .

RUN CGO_ENABLED=0 go build -o dashboard .

EXPOSE 8081

CMD ["/dashboard"]