
# JSHint - v0.10.0

> Documentação para Referência: [https://www.npmjs.org/package/grunt-contrib-jshint](https://www.npmjs.org/package/grunt-contrib-jshint)


## Sobre

JSHint é uma ferramenta de validação de arquivos JavaScript. É importante ressaltar que esse tipo de plugin não garante que seu código está funcionando, que a lógica está correta, garante apenas a presença de boas práticas de desenvolvimento.


## Como aplicá-lo?

> Seu JavaScript validado

Para usar o **JSHint** em seu projeto, é preciso digitar o script abaixo via linha de comando.

`npm install grunt-contrib-jshint --save-dev`


## Visão Global

No arquivo **Gruntfile** do seu projeto, adicione uma seção nomeada como **jshint** para que os objetos sejam passados dentro do método grunt.initConfig(). Confira um exemplo abaixo.

> Configuração

	`jshint: {
    	all: ['Gruntfile.js', 'app/scripts/**/*.js']
  	},`

## Opções

Abaixo segue algumas opções bem interessantes que precisavam ser comentadas.

### JSHintrc: 
Indicaremos ao plugin onde colocamos o nosso arquivo '.jshintrc'. Esse arquivo é um JSON com todas as configurações que escolhemos para validar os nossos arquivos JS.  `jshintrc`


### Reporter: 
Utilizaremos o plugin jshint-stylish para deixarmos o relatório de erros do JSHint mais bonito e organizado. `reporter`


## Site Oficial

* [GruntJS](http://gruntjs.com/)

## Comunidades

* [Repositório Oficial](https://www.npmjs.org/package/grunt-contrib-jshint)
* [Artigo - Qualidade de código em JavaScript](http://tableless.com.br/qualidade-codigo-javascript/)