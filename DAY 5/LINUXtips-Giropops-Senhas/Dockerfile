FROM alpine:3.15.9

LABEL Owner="Rafael Mello"

RUN apk update && apk add --no-cache py3-pip python3 git

RUN git clone https://github.com/badtuxx/giropops-senhas.git

WORKDIR /giropops-senhas

RUN pip install --no-cache-dir -r requirements.txt

ENV REDIS_HOST=127.0.0.1

EXPOSE 5000

CMD flask run --host=0.0.0.0

