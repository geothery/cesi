FROM golang:alpine AS build-env
WORKDIR /go/src/app
COPY . .
RUN CGO_ENABLED=0 go build -a -installsuffix cgo -ldflags '-s' -o /service

FROM scratch
COPY --from=build-env /service /service
ENV MAX_TIME=5
EXPOSE 8080
CMD ["/service"]
