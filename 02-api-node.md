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

### branches, branches, branches!

Eu recmendo que você crie branches para tudo no seu projeto. Cada funcionalidade uma branch. Desse modo, o branch principal, o "main" será sempre um branch estável no projeto. Vou mostrar aqui o processo para você criar o primeiro branch, e depois fica contingo a responsabilidade de criar outros

![image](https://user-images.githubusercontent.com/1509692/214833266-88d7d4fb-dd25-40ed-a774-b3a3d44dee08.png)

Neste novo branch, vamos criar a estrutura inicial do node

### Estrutura inicial do NodeJS

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

A medida que você fizer modificações nos arquivos, pode ir sempre realizando o commit e o push. Ao retornar no github, você verá algo assim:

![image](https://user-images.githubusercontent.com/1509692/214837277-35d8e6e9-948a-4816-94bd-05f2b8cbc19c.png)

O GitHub já entendeu que um novo branch foi criado, e lhe adiciona a possibilidade de realizar um `pull request` que é uma forma de "juntar" o que está no branch novo ao branch main. Veja que o arquivo `package.json` nao está presente no repositório, mas isso é porque está se exibindo o branch `main`. 

![image](https://user-images.githubusercontent.com/1509692/214837748-9d9de292-d330-4705-905a-dfba7407441f.png)

Ao alterar o branch (no detalalhe da seta acima), podemos ver o arquivo `package.json`.

### Voltando ao package.json

Ao abrirmos o arquivo `package.json` no vscode, temos:

![image](https://user-images.githubusercontent.com/1509692/214838631-a2a3adf9-77ea-4f17-bf72-b45abae1c3f8.png)

Temos aqui várias informações sobre o projeto. Por enquanto, vamos dar uma olhada no `scripts`. Tem-se a configuração para "test", nao qual iremos removê-la! Não vamos fazer testes nesse projeto. Vamos trocar "test" para "dev" com o seguinte texto:

![image](https://user-images.githubusercontent.com/1509692/214839254-aa623ee1-9390-4347-ab6a-cc08490532e0.png)

O comando `dev` executa o arquivo `src/index.js` (sim, ainda nao o criamos). Repare na palavra `Debug` logo acima do `scripts`, clique nela para executar o comando `dev`, ocasionando no seguinte erro:

![image](https://user-images.githubusercontent.com/1509692/214839832-e58dd195-0549-44b7-8906-4ae267c42759.png)

Até aqui tudo bem.  O arquivo não existe, é para dar erro mesmo. Você também pode executar o comando pelo terminal, usando o seguinte comando:

![image](https://user-images.githubusercontent.com/1509692/214840764-318ca88d-604e-4d77-b43a-19df397cba4b.png)

### Criando o arquivo index.js

Para que o comando `npm run dev` funcione, precisamos criar o arquivo `src/index.js`. Eu sempre gostei de deixar os arquivos de código na pasta `src` (de source code), e os arquivos e configuração de projeto fora dele. Para mim, fica visualmente melhor. Claro que essa é uma escolha que você pode alterar.

Eu gosto de criar arquivos no próprio vscode. Na aba explorer, clico no `new file` e jpa digito `src/index.js`. O próprio vscode irá criar o diretório src.

![image](https://user-images.githubusercontent.com/1509692/214841799-67814337-3c3c-4124-92be-b6d2e2444f7c.png)

![image](https://user-images.githubusercontent.com/1509692/214841858-3e460968-cf45-4da2-8c69-dd45e2abeba6.png)

![image](https://user-images.githubusercontent.com/1509692/214842000-ea96c496-d6b3-413e-8a21-44655e6c2d76.png)

#### Hello World

No arquivo `src/index.js`, adicionamos uma mensagem de "hello world":

![image](https://user-images.githubusercontent.com/1509692/214842261-c4ebc8c4-8405-4bd4-9c11-f389352cc3e5.png)

Ao executar novamente o comando `npm run dev` no terminal, temos a resposta. Também podemos clicar no botão `Debug` se o arquivo `package.json` estiver aberto:

![image](https://user-images.githubusercontent.com/1509692/214842514-dc2ee31d-1678-4415-a08f-b173cc1d78ef.png)

### Modo "watch"

A partir do Node 18, temos o modo "watch" que vai re-executar o código sempre que houver uma modificação no código fonte. Aletere o `package.json` para:

![image](https://user-images.githubusercontent.com/1509692/214842923-3230b050-0931-4c1b-8958-6e65978506b6.png)

E execute novamente `npm run dev` no terminal. Faça qualquer alteração no arquivo `index.js` e veja o comando sendo executado novamente:

![image](https://user-images.githubusercontent.com/1509692/214843047-cb793cc4-6c3c-4ad8-a476-7c09431791a2.png)

### Finalizando o branch

Temos agora um projeto funcionado, mesmo que seja com um "Hello World". Chegou a hora de comitar & pushar tudo:

![image](https://user-images.githubusercontent.com/1509692/214843425-ee183c8f-bcdb-4f5d-9eef-2fdc1a829998.png)

Retornando ao gitHub, temos:

![image](https://user-images.githubusercontent.com/1509692/214843538-5858e183-3f7f-4cf5-92b4-d6d62acf46c1.png)

Podemos usar o github para criar um pullrequest do branc que criamos para o main. Basta seguir o fluxo. Após fazer o pull request, pode-se deletar o branch. O resultado final é:

![image](https://user-images.githubusercontent.com/1509692/214844350-19142acc-d2d0-4fe1-aace-9bd6a9d3b408.png)

Já no vscode, clique no branch:

![image](https://user-images.githubusercontent.com/1509692/214844576-531e74f8-4fad-46a1-aaf8-7eb1fbd24b93.png)


e selecione o "main". você perceberá que os arquivos package.json e index.js sumiram! Calma:

![image](https://user-images.githubusercontent.com/1509692/214844785-e2d962a2-9b95-405d-b3de-520086b4e6c4.png)

Como podemos ver no detalhe, existem 3 alterações no servidor remoto que precisam ser atualizadas. basta clicar no botão "sync" 🔄 para sincroniar a sua base com a base remota. Assim que você fizer isso, os arquvios estarão atualizados.

![image](https://user-images.githubusercontent.com/1509692/214845171-24a0b22a-e4c8-4963-b212-ee6381b4179e.png)

## Criando o servidor web

Nosso propósito nao é exibir um "hello world" no console. O que precisamos fazer agora é criar uma API que, quando acessarmos o endereço "/hello-world" o navegador responda com a seguinte mensagem:

```json
{ "mensagem": "hello world" }
```

Basicamente, tudo que iremos aprender nesse tutorial é responder uma mensagem (em formato JSON) a uma requisição. Vamos começar então criando um novo branch:

![image](https://user-images.githubusercontent.com/1509692/214847218-dab8aea9-82f3-497a-9278-dd7960bc0a2e.png)

### Adicionando o Expressjs

Para o servidor web, usamos o [ExpressJS](https://expressjs.com/pt-br/). Ele é simples de usar e cumpre bem nosso propósito. Para isso, no terminal, execute o seguinte comando:

![image](https://user-images.githubusercontent.com/1509692/214847616-a48d21bc-a435-4f8b-a6d9-db2945e53c3e.png)

O comando `npm install express` instalou a biblioteca express, e além disso, alterou o arquivo `package.json`, adicionando a configuração de dependencias: 

![image](https://user-images.githubusercontent.com/1509692/214847910-242aa2bc-072b-4ff7-8b8b-561bc30ad389.png)

Com isso, se você quiser usar o projeto em um outro computador, poderá instalar todas as dependencias de uma forma bem simples! veremos isso mais no final do tutorial.

Com o express instalado, podemos alterar o arquivo `src/index.js` adicinando o seguinte código:

```js
var express = require('express');
var app = express()

app.get('/hello-world', function(req, res, next) {
    return res.json({
        mensagem: "hello world"
    });
})

app.listen(3000, function() {
    console.log('Express server listening on port 3000');
})
```

Como instalamos a biblioteca `express`, podemos utilizá-la através do comando `require`. Neste ponto, criamos a variável `app` que é uma instância
do express, e podemos usar essa variável para configurar o que chamamos de "rotas". Por exemplo, `app.get('/hello-world',....` configura uma rota para o acesso
GET à `/hello-world`. ou seja, se digitar no navegador `http://<url>/hello-word`, o código dentro do `app.get()` será executado. Neste caso, o código retorna um `res.json` que é uma forma de retornar *json* a quem o chamou. 

O próximo código é um `app.listen`, que configura a porta 3000 para "ouvir" qualquer requisição. Então, no navegador podemos acessar `http://loscalhost:3000/hello-world` para se obter a resposta `{ mensagem: "hello world" }`

![image](https://user-images.githubusercontent.com/1509692/214862503-ff90cf36-8ee7-42af-a5aa-0671658d29b8.png)


### Configurando o REST Client

![image](https://user-images.githubusercontent.com/1509692/214910635-ad6be264-e3c2-4f9c-a20e-0d6b52035d05.png)

O REST Client é uma extensão do VSCode para que se possa executar chamadas GET (entre outras) diretamente do vscode, sem a necessidade de se utilizar um navegador.

Instale a extensão, e então crie um arquivo chamado `api.http`, inicialmente com o seguinte código:

```
GET http://localhost:3000/hello-world

```

Após criar a instrução GET, surge um link chamado "Send Request" acima do GET. Clique nesse link para obter a resposta, como mostrado a seguir:

![image](https://user-images.githubusercontent.com/1509692/214911527-6db0ccfe-3382-4ef6-a544-61d789ed584f.png)

Veja que foi realizada uma requisição GET a url, e a resposta foi a mesma do que se tivessemos digitado o endereço no navegador.

Vamos fazer uma pequena modificação adicionando a variável "host", da seguinte forma:

```
@host = http://localhost:3000

GET {{host}}/hello-world
```

Assim, não é necessário digitar a url em todas as requisições.

## Criando mais rotas

Como uma API Rest possui muitas rotas, nao é muito legal criar todas elas no arquivo `index.js`. Podemos separar as rotas de acordo com suas funcionalidades. Por exemplo, as rotas de autenticação ficariam no arquivo `auth.js`, as rotas das categorias das tarefas, em `categories`. E assim vai..

Existem algumas dezenas de formas de se fazer isso. Mas, como estamos indo pela forma mais simples
possível, vamos apenas adicionar as rotas manualmente no arquivo `index.js`. Primeiro, crie os seguintes arquivos:

- src/api/auth.js
- src/api/categories.js

Agora, podemos adicionar estas rotas ao arquivo `src/index.js` da seguinte forma

```js
var express = require('express');
var app = express()

app.get('/hello-world', function(req, res, next) {
    return res.json({
        mensagem: "hello world"
    });
})

app.use('/api/auth', require('./api/auth'));

app.listen(3000, function() {
    console.log('Express server listening on port 3000');
})
```

Usamos aqui o método `use` do express para relacionar uma determinada rota "/api/auth" ao arquivo "/api/auth". Se você executar esse código terá um erro, mais ou menos assim:

*TypeError: Router.use() requires a middleware function but got a Object*

Isso acontece porque o Router.use espera uma função na qual ele saiba lidar. E no caso isso nao aconteceu. Vamos editar agora o arquivo `src/api/auth.js` para configurar corretamente o router.

```js
const express = require('express');
const router = express.Router()

router.get('/hello-world', function(req, res, next) {
    return res.json({ message: 'hello world from /api/auth' }); endif
})

module.exports = router
```

O que fizemos aqui iremos fazer em toda a nossa api. Importar o express, pegar a instancia do Router, configurar algumas chamadas, e no final exportar o router pelo `module.exports` para que o require funcione. Apesar de termos `router.get('/hello-world'`, lembre-se que esse arquivo foi adicionado ao router pelo comando `app.use('/api/auth', require('./api/auth'))` no `src/index.js`, então a chamada a api deve ser `/api/auth/hello-world`. 

Vamos editar novamente o arquivo `api.http` adicionando esta rota:

```
@host = http://localhost:3000

GET {{host}}/hello-world

###

GET {{host}}/api/auth/hello-world
```

A respotsa é semelhante a figura a seguir:

![image](https://user-images.githubusercontent.com/1509692/214917789-404ba593-9be8-4320-ba8e-eb0933952f89.png)





