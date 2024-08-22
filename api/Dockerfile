# Build stage
FROM node:18-alpine3.19 AS build

WORKDIR /usr/src/app

# Copiar arquivos relacionados às dependências e instalar dependências
COPY package.json yarn.lock .yarnrc.yml ./
COPY .yarn ./.yarn

# Instalar todas as dependências, incluindo devDependencies
RUN yarn install

# Copiar o restante do código para o diretório de trabalho
COPY . .

# Construir a aplicação
RUN yarn run build && yarn cache clean


# Production stage
FROM node:18-alpine3.19

WORKDIR /usr/src/app

# Copiar apenas os arquivos necessários do estágio de build
COPY --from=build /usr/src/app/dist ./dist
COPY --from=build /usr/src/app/node_modules ./node_modules
COPY --from=build /usr/src/app/package.json ./package.json

EXPOSE 3000

CMD ["yarn", "run", "start:prod"]