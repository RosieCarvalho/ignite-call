## O projeto

Esse projeto realiza integração social com o google para internalizar o google calendar. Todo o back-end é feito no proprio projeto usando as apis do next. o Prisma é usado para conexão de banco de dados.

## uteis

- Uso de hook form bem completo em: src\pages\register\time-intervals
- função para retornar dias das semanas: src\utils
- função para retornar hora em minutos: src\utils
- usar dados da session no back-end do next: unstable_getServerSession

## Bibliotecas

- React-hook-form
  - validação de form e uso de transformação com zod
  -

```bash
   npm i react-hook-form @hookform/resolvers zod
```

- Prisma

  - ferramenta pra comunicação com o banco de dados
  - Comando de instalação da interface de linha de comando do Prisma: npm i prisma -D

    ```bash
    npm i prisma -D
    ```

  - Comando de instalação da dependência que iremos utilizar na nossa aplicação:

    ```bash
      npm i @prisma/client
    ```

  - Comando para iniciar o Prisma:

    ```bash
      npx prisma init --datasource-provider SQLite
    ```

  - Comando pra rodar a migration -(migration é como um comando do git)

    ```bash
    npx prisma migrate dev
    ```

  - Comando pra rodar o Prisma Studio:

    ```bash
    npx prisma studio
    ```

    -cookies : para salvar informações de usuário

    - Comando de instalação do nookies: npm i nookies
      ```bash
      npm i nookies
      ```
    - Comando para a instalação das tipagens da biblioteca
      ```bash
      npm i @types/cookie -D
      ```

- dayjs

  - para trabalhar com datas

- react query

```bash
 npm i @tanstack/react-query
```

## autenticação social

- **oAuth**

  - protocolo de autenticação usando next-auth

- **Autenticação com google**

  passo 1: configuração no console.cloud google

  - criar projeto no console.cloud da google: https://console.cloud.google.com/welcome?hl=pt-br&project=ageless-parity-150413
  - editar a tela de permissão do oauth que fica dentro de APIS e serviços
  - ir em credenciais e criar uma credencial de client oauth
    o ID do cliente E Chave secreta do cliente é fundamental para conectar a aplicação. Guarde isso! é recomendavel criar no .env uma variavel para ela
  - ativar API e serviços: para usar o calendario é necessário ir ativa-lo aqui

  passo 2: configurando no projeto o next-auth

  - src\pages\api\auth\[...nextauth].ts
  - https://next-auth.js.org/getting-started/example
  - escopos
    - é necessario para definir algumas permissões

- **Salvando informações do login no banco de dados (PRISMA)**

  - https://authjs.dev/getting-started/adapters/prisma
  - adapters: é um ponto de conexão entre o banco e a aplicação(next-auth).
    - podemos criar nossos proprios adapters reescrevendo as funções do next-auth e assim conectar com qualquer banco de dados. Neste projeto conectamos com o prisma
  - neste projeto criamos o nosso proprio adapters: src\lib\auth\prima-adapter.ts

- **Integração com API DA GOOGLE**
  - instalar:
    ```bash
    npm i googleapis
    ```
  - configuração: google.ts
    - aqui está a lógica de conexão com api do google
  - inserindo eventos no calendário do google: schedule.api

## docker

- gerar novo container

  -docker run --name mysql -e MYSQL_ROOT_PASSWORD=docker -p 3306:3306 mysql:latest
  -docker run --name postgres -e POSTGRES_PASSWORD=docker -p 5432:5432 -d postgres

- rodar o container
  -docker start -nome do banco- (no caso aqui é mysql)

## SEO

- doc: https://github.com/garmeeh/next-seo?tab=readme-ov-file#usage
- instalar: npm install next-seo
- uso: #seo

## DEPLOY

**BANCO DE DADOS**

- para hospedar : https://neon.tech/
  -mudando o projeto para outro banco: https://efficient-sloth-d85.notion.site/Ignite-Call-Postgres-dev-e-prod-bd105befe0ab411cb7074aad72819613

  - preparar prisma para subir: npx prisma migrate deploy

  **APLICACAÇÃO**

- para hospedar: vercel
- instal: https://vercel.com/docs/cli
