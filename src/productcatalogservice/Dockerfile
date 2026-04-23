FROM golang:1.21-alpine AS builder
WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download
COPY . .
RUN go build -o productcatalogservice .

FROM alpine:3.18
WORKDIR /app
COPY --from=builder /app/productcatalogservice .
COPY --from=builder /app/products.json .
EXPOSE 3550
CMD ["./productcatalogservice"]
