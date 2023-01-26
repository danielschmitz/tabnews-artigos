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









