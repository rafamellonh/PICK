### Transformar o app Senhas em um Container.

* Crie o arquivo Dockerfile para compilar a imagem com as informações do app.

#####Dockerfile

``` 

FROM python:3.11

WORKDIR /app
COPY requirements.txt .
COPY app.py .
COPY templates templates/
COPY static static/

RUN pip install --no-cache-dir -r requirements.txt

EXPOSE 5000

CMD [ "flask", "run", "--host=0.0.0.0" ]


``` 

Compile a imagem e crie o container<br>
``` docker image build -t giropops-senhas:1.0 . ``` <br>
``` docker container run -d -p 5000:5000 --name giropops-senhas01 giropops-senhas:1.0 ```

Crie um container temporário para o Redis

```docker run -d --name redis -p 6379:6379 redis ```

