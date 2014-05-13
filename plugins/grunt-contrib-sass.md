
# grunt-contrib-sass - v0.7.3 ![GruntJS](https://travis-ci.org/gruntjs/grunt-contrib-sass.png)

> Documentação para Referência: [https://npmjs.org/package/grunt-contrib-sass](https://npmjs.org/package/grunt-contrib-sass)


## Sobre

Sass é um pré-processador que acrescenta regras aninhadas, variáveis, funções, herança, seletor e muito mais a CSS. Arquivos Sass compila o CSS padrão para usar em seu site ou aplicativo. O **grunt-contrib-sass** é nada mais do que um plugin do pré-processador que vai permitir você usar o SASS para suas tarefas específicas.

## Como aplicá-lo?

> CSS MELHORADO

Para usar o **grunt-contrib-sass** em seu projeto, é preciso digitar o script abaixo via linha de comando.

`npm install grunt-contrib-sass --save-dev`

OBS: Esta tarefa exige que você tenha Ruby e Sass instalado. Se você está no OS X ou Linux, você provavelmente já tem o Ruby instalado; testar com `ruby-v` em seu terminal. Quando você tiver confirmado que você tem o Ruby instalado, use `gem install sass` ou `sudo gem install sass` 

## Visão Global

No arquivo **Gruntfile** do seu projeto, adicione uma seção nomeada como **sass** para que os objetos sejam passados dentro do método grunt.initConfig(). Confira um exemplo abaixo.

> Configuração

	`grunt.initConfig({
	  sass: {                              
	    dist: {                            
	      options: {                       
	        style: 'expanded'
	      },
	      files: {                         
	        'main.css': 'main.scss',      
	        'widgets.css': 'widgets.scss'
	      }
	    }
	  }
	});

	grunt.loadNpmTasks('grunt-contrib-sass');

	grunt.registerTask('default', ['sass']);`


> Compilação e Minificação

	`grunt.initConfig({
	  sass: {
	    dist: {
	      files: {
	        'main.css': 'main.scss'
	      }
	    }
	  }
	});`

## Opções

Abaixo segue algumas opções bem interessantes que precisavam ser comentadas.

### Debug SASS

Ultilizamos essas configurações para ativarmos o debug do SASS por meio do <a href="https://addons.mozilla.org/en-US/firefox/addon/firesass-for-firebug/">fireSASS</a><br>

**Code:** `debugInfo` <br>
**Tipo:** `boolean` <br>
**Padrão:** `false`

### SourceMap

Ativarmos sourcemap para os browsers que suportam essa tecnologia. <br/>

**Code:** `sourcemap` <br>
**Tipo:** `boolean` <br>
**Padrão:** `false`

> Lembrando que o processamento fica mais lento utilizando essas opções.

## Site Oficial

* [GruntJS](http://gruntjs.com/)

## Comunidades

* [Repositório Oficial](https://www.npmjs.org/package/grunt-contrib-sass)