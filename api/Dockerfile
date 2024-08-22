# Build stage
FROM node:18-alpine3.19 AS build

WORKDIR /usr/src/app

# Copiar os arquivos necessários para instalar as dependências
COPY package.json yarn.lock .yarnrc.yml ./
COPY .yarn ./.yarn

# Instalar todas as dependências, incluindo devDependencies
RUN yarn

# Copiar o restante do código para o diretório de trabalho
COPY . .
# Construir a aplicação
RUN yarn run build

# Reduzir o tamanho da imagem removendo devDependencies
RUN yarn workspaces focus --production && yarn cache clean

# Production stage
FROM node:18-alpine3.19

WORKDIR /usr/src/app

# Copia apenas os arquivos necessários do estágio de build
COPY --from=build /usr/src/app/dist ./dist
COPY --from=build /usr/src/app/node_modules ./node_modules

EXPOSE 3000

CMD ["yarn", "run", "start"]