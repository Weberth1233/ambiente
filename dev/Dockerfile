# Usando a imagem base Debian 12
FROM debian:12

# Atualizando e instalando dependências necessárias
RUN apt-get update && apt-get install -y \
  curl \
  gnupg \
  lsb-release \
  ca-certificates \
  && curl -fsSL https://deb.nodesource.com/setup_16.x | bash - \
  && apt-get install -y nodejs \
  && apt-get clean

# Diretório de trabalho dentro do container
WORKDIR /app

# Instalando dependências do projeto
COPY package.json /app
COPY package-lock.json /app
RUN npm install

# Copia o código da aplicação para dentro do container
COPY . /app

# Expondo a porta onde o app React vai rodar
EXPOSE 3000

# Comando para iniciar a aplicação em modo de desenvolvimento
CMD ["npm", "start"]