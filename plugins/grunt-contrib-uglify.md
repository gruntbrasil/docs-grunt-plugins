# grunt-contrib-uglify v0.4.0 [![Build Status: Linux](https://travis-ci.org/gruntjs/grunt-contrib-uglify.png?branch=master)](https://travis-ci.org/gruntjs/grunt-contrib-uglify) <a href="https://ci.appveyor.com/project/gruntjs/grunt-contrib-uglify"><img src="https://ci.appveyor.com/api/projects/status/ybtf5vbvtenii561/branch/master" alt="Build Status: Windows" height="18" /></a>

> Documentação para Referência: [https://github.com/gruntjs/grunt-contrib-uglify](https://github.com/gruntjs/grunt-contrib-uglify)


## Sobre

O grunt-contrib-uglify é um plugin para minificar seus arquivos. Pode se dizer que foi feito para facilitar e dar uma agilizada em seu projeto. Com **grunt-contrib-uglify** você pode estar minificando arquivos como: **CSS**, **JS** e até **HTML**. 


## Como aplicá-lo?

> MINIFICAÇÃO

Para usar o **grunt-contrib-uglify** em seu projeto, é preciso digitar o comando abaixo via Shell.

`npm install grunt-contrib-uglify --save-dev`


## Visão Global

No arquivo **Gruntfile** do seu projeto, adicione uma seção nomeada como **uglify** para que os objetos sejam passados dentro do método grunt.initConfig(). Confira um exemplo abaixo.

  	grunt.initConfig({
	    uglify : {
	      options : {
	        mangle : false
	      },

	      my_target : {
	        files : {
	          'assets/js/main.js' : [ 'assets/_js/scripts.js' ]
	        }
	      }
	    }
  	});


## Opções

Esta é a tarefa principal: [UglifyJS2](https://github.com/mishoo/UglifyJS2), por isso, considero a documentação UglifyJS como leitura obrigatória para a configuração avançada.

### mangle

**Tipo:** `Boolean` `Object` <br/>
**Valor padrão:** `{}`

Ligar ou desligar deturpações com as opções padrão. Se um objeto é especificado, ele é passado diretamente para:
`ast.mangle_names()` e `ast.compute_char_frequency()` (imitando o comportamento de linha de comando).

### compress

**Tipo:** `boolean` `Object` <br/>
**Valor padrão:** `{}`

Ativar ou desativar a compactação da fonte com opções padrão. Se um objeto é especificado, ele é passado como opção para
`UglifyJS.Compressor()`.

### sourceMap

**Tipo:** `boolean` <br/>
**Valor padrão:** `false`

Se for verdade, um arquivo de origem mapa será gerado no mesmo diretório que o arquivo dest. Por padrão, ele terá o mesmo nome de base como a:

`dest` arquivo, mas com a extensão `.map`

## Artigos

* [GruntJS - Por onde Começar](http://www.voltsdigital.com.br/labs/gruntjs-por-onde-comecar/)
* [Grunt: você deveria estar usando](http://tableless.com.br/grunt-voce-deveria-estar-usando/)

## Site Oficial

* [GruntJS](http://gruntjs.com/)

## Comunidades

* [GruntJS Brasil](https://www.facebook.com/groups/gruntbrasil/?fref=ts)
* [Grunt Brasil - Repositórios git](https://github.com/gruntbrasil/)