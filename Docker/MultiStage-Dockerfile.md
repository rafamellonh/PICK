FROM golang:1.18 as buildando
WORKDIR /app
COPY . ./
RUN go mod init hello
RUN go build -o /app/hellp

FROM alpine:3.15.9
COPY --from=buildando /app/hello /app/hello
ENV APP="Hello_world"
ARG GIROPOPS="strigus"
RUN echo "chamando o ARG " $GIROPOPS"
CMD ["/app/hello"]
