FROM node:18-slim 
# FROM pega a imagem: e a versão dela
WORKDIR /usr/src/app
# WORKDIR seta um lugar de trabalho, caso não exista ela cria
COPY package.json yarn.lock .yarnrc.yml /usr/src/app/
COPY .yarn ./.yarn
# Copia o arquivo package.json para o diretório de trabalho
RUN yarn
# Executa o comando yarn
COPY . /usr/src/app/
# Copia todos os arquivos para o diretório de trabalho
RUN yarn run build
# Inicia a construção do yarn
EXPOSE 3000
# Exponha a porta que o container irá usar
CMD [ "yarn","run","start" ]