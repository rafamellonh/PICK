FROM ubuntu

RUN NODE_MAJOR=20

RUN apt update && \
    apt install -y ca-certificates curl gnupg && \
    mkdir -p /etc/apt/keyrings && \
    curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && \
    apt update && \
    apt install -y nodejs



WORKDIR /app    
COPY . .

RUN npm install

ENTRYPOINT ["node", "server.js"]

