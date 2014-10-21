
# validation - W3C html validation

> Documentação para Referência: [https://npmjs.org/package/grunt-html-validation](https://npmjs.org/package/grunt-html-validation)


## Sobre

O **validation** é um plugin com grandes vantagens e é o que todos nós esperávamos. Ele trabalha validando o seu código HTML de acordo com as especificações exigidas pela Organização W3C, ou seja, 100% padronizado.

## Como aplicá-lo?

> VALIDANDO SEU HTML

Para usar o **validation** em seu projeto, é preciso digitar o script abaixo via linha de comando.

`npm install grunt-html-validation --save-dev`

OBS: Esta tarefa exige que você tenha NODE instalado para baixar os pacotes NPM's.

## Usando o Plugin

No arquivo **Gruntfile** do seu projeto, adicione uma seção nomeada como **validation** para que os objetos sejam passados dentro do método grunt.initConfig(). Confira um exemplo abaixo.

> Configuração

	validation : {
	    options : {
	        reset : true,
	        reportpath : false
	    },
	    files : {
	        src : 'dev/index.html'
	    }
	}

	grunt.loadNpmTasks('validation');

	grunt.registerTask('default', ['validation']);


## Opções

* A opção `reset: true` é referente ao cache. Já tive problemas de cache com esse plugin, dessa maneira, vamos ignorar o cache e sempre passar nosso HTML pelo validador.

* Já `reportpath : false` não vai criar um arquivo de log referente aos problemas encontrados.

## Site Oficial

* [GruntJS](http://gruntjs.com/)
* [Repositório Oficial](https://www.npmjs.org/package/grunt-html-validation)