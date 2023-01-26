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




