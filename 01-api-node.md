# Criando uma API minimalista em NodeJS

O objetivo desse tutorial é criar uma API NodeJS para um simples cadastro de tarefas, mas que pode ser expandida para uma API completa de qualquer tipo de sistema. 

Esta api deverá possuir os seguintes requisitos:

- Ser o mais minimalista possível
- Integrada ao Github desde o início
- Possuir um serviço de autenticação JWT
- Possuir bancos de dados diferentes entre o servidor de desenvolvimento e o servidor de produção
- Mais?

## Escolhendo as tecnologias

O NodeJS é uma ótima forma de inicar nossos estudos na criação de uma API. Ele possui todos os requisitos básicos para isso,
além de ser de fácil aprendizagem e com um amplo leque de bibliotecas pronto para uso. Neste tutorial utilizaremos o ExpressJS
como servidor web, e o Knex como "query builder". O knex nao é uma ferramente ORM, é apenas uma forma de montar queries SQL 
de uma forma um pouco mais abstrata. 


