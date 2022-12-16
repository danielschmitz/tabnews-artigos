# Crie estruturas de banco de dados com o dbdiagram.io

Durante muitos anos, sempre que tenho a necessidade de criar uma estrutura para banco de dados, envolvendo tabelas e seus relacionamentos, eu lembro do [dbdiagram.io](dbdiagram.io)

Acessando o link acima, temos a demostração básica do que a app é capaz de fazer. 

![](https://user-images.githubusercontent.com/1509692/208109252-a14ce2dd-3d21-4011-8f10-3e1eb5d9c487.png)

Do lado ESQUERDO, temos uma representação em texto das tabelas. E do lado DIREITO, o diagrama. O que todos nós devs adoramos fazer? **Escrever código!** E o dbdiagram foi feito especialmente para nós

## Começando

Você pode criar uma conta para assim poder guardar seus diagramas, ou começar imediatamente a criar um diagrama clicando no botão `go to app`. Ao clicar nele, um diagrama é prontamente criado. Vamos então "limpar" esse diagrama da melhor forma, selecionando todo o texto à esqueda da tela e apertando delete (ou backspace se for for contra as regras da sociedade)

Temos agora um diagrama vazio, no limbo:

![](https://user-images.githubusercontent.com/1509692/208110090-99c58f2d-ba85-42dc-b64d-0da9bc920da4.png)

## Criando o tabnews

Como o site é open source, podemos dar uma 👀 na sua estrutura de tabelas e fazer um diagrama de tabelas. Fica aqui o "dever de casa" para você fazer o diagrama e mandar um PR para o repositório, assim é possível ver de forma visual a estrutura das tabelas. Bora lá! 

Ao acessar [o primeiro migration](https://github.com/filipedeschamps/tabnews.com.br/blob/main/infra/migrations/1632278997051_create-user-table.js) que cria a tabela users, podemos extrair os seguintes campos:

- id (uuid)
- username (varchar)
- email (varchar)
- password (varchar)
- features (varchar)
- created_at (date)
- updated_at (date)

Vamos então criar essa tabela no dbdiagram:


![](https://user-images.githubusercontent.com/1509692/208112719-0aa64e56-b892-4abe-957d-5d2db64ad21a.png)

Asssim que começamos a escrever a estrutura da tabela, o seu diagrama começa a ser desenhado. Eu nao vou colar aqui a estrutura em modo texto, para que você mesmo possa digitar e ver como a ferramenta funciona. 


