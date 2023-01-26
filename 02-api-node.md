# Criando uma API minimalista em NodeJS

O objetivo desse tutorial é criar uma API NodeJS para um simples cadastro de tarefas, mas que pode ser expandida para uma API completa de qualquer tipo de sistema. 

Esta api deverá possuir os seguintes requisitos:

- Ser o mais minimalista possível
- Integrada ao Github desde o início
- Possuir um serviço de autenticação JWT
- Possuir bancos de dados diferentes entre o servidor de desenvolvimento e o servidor de produção
- Ser Deploy ready, ou seja. Fez o PUSH, o deploy é gerado. Podemos usar a vercel.com para isso
- Mais?

## Escolhendo as tecnologias

O NodeJS é uma ótima forma de inicar nossos estudos na criação de uma API. Ele possui todos os requisitos básicos para isso,
além de ser de fácil aprendizagem e com um amplo leque de bibliotecas pronto para uso. Neste tutorial utilizaremos o ExpressJS
como servidor web, e o Knex como "query builder". O knex nao é uma ferramente ORM, é apenas uma forma de montar queries SQL 
de uma forma um pouco mais abstrata. 

Para o deploy, vamos utilizar a Vercel. Isso, aquela do next.js. Ela também roda o NodeJS.

Para banco de dados, vamos usar: 

- No modo de desenvolvimento, vamos usar o sqlite3
- No modo de produção, vamos usar o postgreSQL


## Antes de começar

Na sua máquina, você precisa do seguinte:

- NODEJS: versão 18 pra cima
- GIT:  com aquele git bash (Quando eu falar "abra o terminal", é o git bash)
- Uma conta no github
- VSCODE: editor de textos 

## Começando

### Criando o repositório

Abra o github e clique em "New Repository". Crie o seu repo com os seguintes parametros:

![image](https://user-images.githubusercontent.com/1509692/214823491-3ada304a-aaa5-49b6-8886-c84a32791a8b.png)

Como podemos ver, escolhemos:

- O nome do projeto: api-node
- Uma descrição do projeto
- Definimos o projeto como público (melhor para seu curriculo)
- Selecionamos para adicionar um README.md
- Selecionaos para adcionar um .gitignore com NODE
- Selecionaos a licença MIT.

Após criar o repositório, você verá algo assim:

![image](https://user-images.githubusercontent.com/1509692/214824458-e6e9b263-a69e-421e-b573-c38467e320a0.png)

### Clonando o respositório

Clique no botão verdinho `Code` e então verifique se a opção `https` está selecionada e copie a url 

![image](https://user-images.githubusercontent.com/1509692/214824970-ed8936ba-4769-4ec1-8a82-5e9da71d5c9b.png)

Abra o terminal (Git bash) e digite:

```
git clone <url do seu repositório>
```

![image](https://user-images.githubusercontent.com/1509692/214825183-3ae6d793-2587-4619-81d8-264546d2fb85.png)

Entre no diretório `api-node` recem criado e faça um `ls` para ver os arquivos:

![image](https://user-images.githubusercontent.com/1509692/214825335-4f9d7bb4-0319-4239-b72b-4783baff92c3.png)

Como podemos ver, os arquivos iniciais do projeto foram copiados para a sua maquina, e você está no branch `main`

## branches, branches, branches!

Eu recmendo que você crie branches para tudo no seu projeto. Cada funcionalidade uma branch. Desse modo, o branch principal, o "main" será sempre um branch estável no projeto. Vou mostrar aqui o processo para você criar o primeiro branch, e depois fica contingo a responsabilidade de criar outros

![image](https://user-images.githubusercontent.com/1509692/214833266-88d7d4fb-dd25-40ed-a774-b3a3d44dee08.png)

Neste novo branch, vamos criar a estrutura inicial do node

## Estrutura inicial do NodeJS

O NodeJS, quando instalado, traz o pacote `NPM` que pode ser usado para algumas funcionalidades bem interessantes. Uma delas é criar o arquivo `package.json` que é usado para estruturar o seu projeto "Node", contendo informações do projeto e bibliotecas usadas. Para criar esse arquivo, utilize o comando `npm init`.

![image](https://user-images.githubusercontent.com/1509692/214834838-4bf3aff9-4072-4a3a-b8d9-7c006e37a0e8.png)

Após responder algumas questões, o arquivo `package.json` é criado! Para vê-lo, vamos usar o vscode:

![image](https://user-images.githubusercontent.com/1509692/214835302-5de0b8e9-2185-42ab-b3be-569ead574ec1.png)

### VSCode e Git

O comando `code .` dentro do diretório `api-node` abre o Visual Studio Code, semelhante a figura a seguir:

![image](https://user-images.githubusercontent.com/1509692/214836193-fd3933c1-3043-4208-9793-c99d437cd17b.png)

As setas indicam informações sobre o Git. La em baixo temos o branch ativo, na direita a abinha "git" e o nome `package.json` está em verde porque indica que um arquivo está modificado.

Ao clicar na abinha `git`, temos:

![image](https://user-images.githubusercontent.com/1509692/214836552-08c9ed6e-733a-4b0e-a0ee-1ad87bd66a52.png)

Adicionamos um comentário e clicamos no botão `Commit`. Para enviar todas essas informações ao github, podemos pelo próprio VScode clicar no botão `publish`:

![image](https://user-images.githubusercontent.com/1509692/214836955-3b145feb-3fbe-401b-965e-201c3e4825d9.png)














