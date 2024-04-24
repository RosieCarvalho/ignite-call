## O projeto

Esse projeto realiza integração social com o google para internalizar o google calendar. Todo o back-end é feito no proprio projeto usando as apis do next. o Prisma é usado para conexão de banco de dados.

## Bibliotecas

- React-hook-form
  - validação de form com zod

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

## autenticação social

- oAuth:

  - protocolo de autenticação usando next-auth

- autenticação com google

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

- salvando informações do login no banco de dados (PRISMA)
  - https://authjs.dev/getting-started/adapters/prisma
  - adapters: é um ponto de conexão entre o banco e a aplicação(next-auth).
    - podemos criar nossos proprios adapters reescrevendo as funções do next-auth e assim conectar com qualquer banco de dados. Neste projeto conectamos com o prisma
  - neste projeto criamos o nosso proprio adapters: src\lib\auth\prima-adapter.ts
