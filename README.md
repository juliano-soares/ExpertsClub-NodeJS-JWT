# Fundamentos de JWT para uma autenticação mais segura

O JWT é amplamente utilizado como uma forma de autenticação, porém, se não tivermos o conhecimento necessário e aplicarmos algumas boas práticas, esta forma de autenticação pode ter falhas que comprometem a segurança das nossas aplicações e dos nossos dados.

Nesta aula implementamos uma autenticação do 0, vendo alguns erros comuns e, em pouco tempo, aplicamos algumas práticas que aumentam muito a segurança no nosso backend.

## Rodando o projeto

Este projeto consiste de uma API feita em Node.js que consome um banco PostgreSQL. Há um arquivo `.nvmrc` no projeto caso queira realizar a instalação usando o [nvm](https://github.com/nvm-sh/nvm).

Para rodar o projeto é necessário rodar um banco PostgreSQL, sugiro o uso do docker e docker-compose. O projeto já contém um arquivo do docker-compose, então basta usar o seguinte comando:

`docker-compose up`

Usei o dotenv para variáveis de ambiente, então pode-se renomear o arquivo `.env.example` para `.env` e aproveitar as variáveis de ambiente de lá. Por padrão elas apontam para o banco PostgreSQL so docker-compose.

O próximo passo é instalar as depêndencias:

`npm install`

Depois é necessário rodar a migration para criar as tabelas no banco:

`npm run sequelize:migrate`

E então pode-se rodar com nodemon:

`npm run dev`

Para facilitar os testes dos endpoints, pode ser usado o arquivo `JWT.postman_collection.json`. Também utilizao bastante o debugger de JWT disponível [aqui](https://jwt.io/).

## Comandos para criação de chaves privada e pública (testados no MacOS)

```
openssl genrsa -out private-key.pem 2048 
openssl rsa -in private-key.pem -pubout -out public-key.pem
```

Caso queira usar chaves previamente geradas, copie o arquivo `.env.example` para o arquivo `.env`. Mas lembre-se: **Não** use essas chaves em produção, **apenas** para teste.
