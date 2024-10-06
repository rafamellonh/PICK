FROM ubuntu

LABEL Owner="Rafael Mello"

RUN git clone https://github.com/badtuxx/giropops-senhas.git

RUN apt update && apt install redis pip -y

RUN cd giropops-senhas/

RUN pip install --no-cache-dir -r requirements.txt

ENV REDIS_HOST=localhost

RUN flask run --host=0.0.0.0

EXPOSE 80