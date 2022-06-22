FROM golang:1.18 as build

WORKDIR /go/src/app
COPY . .

RUN go mod download
RUN go vet -v
RUN go test -v

RUN CGO_ENABLED=0 go build -o /go/bin/app
# Reference : https://github.com/aquasecurity/fanal/blob/main/secret/builtin-allow-rules.go
FROM gcr.io/distroless/static-debian11
COPY /data/*.pem /usr/local/go
COPY /data/cloud-key.pub /usr/local/go
COPY /data/cloud-key /usr/local/go

COPY --from=build /go/bin/app /
CMD ["/app"]