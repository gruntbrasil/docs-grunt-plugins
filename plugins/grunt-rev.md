# grunt-rev [![Build Status](https://travis-ci.org/cbas/grunt-rev.png)](https://travis-ci.org/cbas/grunt-rev)

> Documentação oficial: [https://github.com/cbas/grunt-rev](https://github.com/cbas/grunt-rev)

## Sobre

O grunt-rev é um plugin para versionar arquivos estáticos através do uso de **hashes**.

Use a tarefa **rev** juntamente com **yeoman / grunt-usemin** para invalidação de cache de arquivos estáticos em seu aplicativo. Isso permite que eles sejam armazenados em cache para sempre pelo navegador.

## Visão Global

No arquivo **Gruntfile** do seu projeto, adicione uma seção nomeada como **rev** para que os objetos sejam passados dentro do método `grunt.initConfig()`.

  	grunt.initConfig({
	  rev: {
	    options: {
	      algorithm: 'md5',
	      length: 8
	    },
	    assets: {
	      files: [{
	        src: [
	          'img/**/*.{jpg,jpeg,gif,png}',
	          'fonts/**/*.{eot,svg,ttf,woff}'
	        ]
	      }]
	    }
	  },
	})


## Opções

### options.algorithm

**Tipo:** `String` <br/>
**Valor padrão:** `md5`

`algorithm` é dependente dos algoritmos suportados pela versão do OpenSSL na plataforma. 

**Exemplos:** `sha1`, `md5`, `sha256`, `sha512`, etc. Em versões recentes, openssl `list-message-digest-algorithms` exibirá os algoritmos de resumo disponíveis.

### options.length

**Tipo:** `Number` <br/>
**Valor padrão:** `8`

O número de caracteres do **hash** que servirá como prefíxo para o nome do arquivo com extensão.

## Exemplos

#### Básico

Isso vai mudar o nome `app.js` e `app.css` utilizando um **hash** com 8 caractéres. 

**Ficando assim:** `js/9becff3a.app.js` e `css/ae35dd05.app.css`. 

*O valor de hash depende do conteúdo do arquivo.*

	grunt.initConfig({
	  rev: {
	    files: {
	      src: ['scripts/app.js', 'css/app.css']
	    }
	  }
	})


#### Customizada

Alterar o algoritmo ou o comprimento dos nomes dos arquivos gerados. Note que a tarefa `usemin` requer pelo menos um caractere hexadecimal *anycase* para prefixar o nome do arquivo.

	grunt.initConfig({
	  rev: {
	    options: {
	      algorithm: 'sha1',
	      length: 4
	    },
	    files: {
	      src: ['**/*.{js,css,png,jpg}']
	    }
	  }
	})

## Licença

MIT License • © Sebastiaan Deckers
