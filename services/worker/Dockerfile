FROM golang:1.23

WORKDIR /app

COPY go.* ./

RUN go mod download 

COPY . .

RUN CGO_ENABLED=0 go build -o /worker .

EXPOSE 8090

CMD ["/worker"]