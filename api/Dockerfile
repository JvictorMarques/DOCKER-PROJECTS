FROM node:18-slim 
# FROM pega a imagem: e a versão dela
WORKDIR /usr/src/app
# WORKDIR seta um lugar de trabalho, caso não exista ela cria
COPY package.json yarn.lock .yarnrc.yml /usr/src/app/
# Copia o arquivo package.json yarn.lock .yarnrc.yml para o diretório de trabalho
COPY .yarn ./.yarn
# Copia a pasta .yarn para um novo diretorio chamado .yarn dentro da pasta /usr/src/app
# Boa prática quando for copiar pastas use outra linha com copy
RUN yarn
# Executa o comando yarn
COPY . /usr/src/app/
# Copia todos os arquivos para o diretório de trabalho
RUN yarn run build
# Inicia a construção do yarn
EXPOSE 3000
# Exponha a porta que o container irá usar
CMD [ "yarn","run","start" ]