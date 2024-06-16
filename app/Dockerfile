# Estágio de construção
FROM node:18 AS builder

# Crie e defina o diretório de trabalho
WORKDIR /usr/src/app

# Copie os arquivos package*.json para o diretório de trabalho
COPY package*.json ./

# Instale as dependências
RUN npm install

# Copie o restante dos arquivos da aplicação
COPY . .

# Estágio de execução
FROM node:18-slim

# Crie e defina o diretório de trabalho
WORKDIR /usr/src/app

# Copie os artefatos construídos do estágio anterior
COPY --from=builder /usr/src/app .

# Exponha a porta que a aplicação irá rodar
EXPOSE 3030

# Comando para iniciar a aplicação
CMD ["node", "index.js"]
