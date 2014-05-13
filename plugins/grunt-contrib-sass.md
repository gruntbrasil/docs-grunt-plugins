# grunt-contrib-sass - Versão 3.3

> Documentação para Referência: [https://npmjs.org/package/grunt-contrib-sass](https://npmjs.org/package/grunt-contrib-sass)


## Sobre

O **grunt-contrib-sass** é nada mais do que um plugin de pré-processador para dar mais facilidade no desenvolvimento de seu projeto, permitindo criação de variáveis, declaração de condições e dentre outros benefícios. Com esse plugin o pré-processador a ser ultilizado é o **SASS**. Existem outros plugins de pré-processadores usados no GruntJS como **LESS**, **Stylus**, **Jade** e entre outros que veremos mais a frente.


## Como aplicá-lo?

> CSS MELHORADO

Para usar o **grunt-contrib-sass** em seu projeto, é preciso digitar o script abaixo via linha de comando.

`npm install grunt-contrib-sass --save-dev`

OBS: Se seu terminal for um Mac OS X, por padrão já vem o Ruby instalado, porém se for Windows é preciso instalar o Ruby e os recursos de SASS. Para instalar esses recursos é preciso: se for root `gem install sass` ou usar `sudo gem install sass`. 

## Visão Global

No arquivo **Gruntfile** do seu projeto, adicione uma seção nomeada como **sass** para que os objetos sejam passados dentro do método grunt.initConfig(). Confira um exemplo abaixo.


  	grunt.initConfig({
		sass : {
		    dist : {
		        files : {
		            'dev/css/main.css': 'dev/sass/main-sass.scss'
		        },
		        options : {
		            debugInfo : true,
		            sourcemap : true
		        }
		    }
		}
  	});


## Opções

Abaixo segue algumas opções bem interessantes que precisavam ser comentadas.

### Debug SASS

**Code:** `debugInfo` - Ultilizamos essas configurações para ativarmos o debug do SASS por meio do <a href="https://addons.mozilla.org/en-US/firefox/addon/firesass-for-firebug/">fireSASS</a><br>

### SourceMap

**Code:** `sourcemap` - ativarmos sourcemap para os browsers que suportam essa tecnologia. <br/>

> Lembrando que o processamento fica mais lento utilizando essas opções.


## Artigos

## Site Oficial

* [GruntJS](http://gruntjs.com/)

## Comunidades

* [Repositório Oficial](https://www.npmjs.org/package/grunt-contrib-sass)