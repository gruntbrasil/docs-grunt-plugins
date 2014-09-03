# grunt-contrib-htmlmin v0.3.0 [![Build Status: Linux](https://travis-ci.org/gruntjs/grunt-contrib-htmlmin.png?branch=master)](https://travis-ci.org/gruntjs/grunt-contrib-htmlmin)

> Documentação para referência [https://www.npmjs.org/package/grunt-contrib-htmlmin](https://www.npmjs.org/package/grunt-contrib-htmlmin)

## Sobre
o plugin **grunt-contrib-htmlmin** minifica seus arquivos HTML.

## Iniciando
Este plugin necessita do Grunt `~0.4.0`

Se você nunca usou o [Grunt](http://gruntjs.com) antes, verifique o [Guia de Introdução](https://github.com/gruntbrasil/grunt-docs/blob/pt-br/Getting-started.md) que contém explicação de como criar um arquivo Gruntfile, bem como instalar e usar plugins no Grunt.

Se você já está familiarizado com esse processo, você pode instalar o plugin com o seguinte comando:

```shell
npm install grunt-contrib-htmlmin --save-dev
```
Para habilitar o plugin, basta inserir este comando dentro do seu arquivo Gruntfile:
```js
grunt.loadNpmTasks('grunt-contrib-htmlmin');
```


## A tarefa "Htmlmin"
Execute esta tarefa com o comando: _**`grunt htmlmin`**._

Este plugin minifica HTML usando o [html-minifier](https://github.com/kangax/html-minifier). Você pode reportar possíveis bugs [aqui](https://github.com/kangax/html-minifier/issues/new).

### Opções

Veja as opções do html-minifier [aqui](https://github.com/kangax/html-minifier#options-quick-reference).

#### Exemplo de configuração

```javascript
grunt.initConfig({
  htmlmin: {                                     // Tarefa
    dist: {                                      // Alvo
      options: {                                 // opções
        removeComments: true,
        collapseWhitespace: true
      },
      files: {                                   // Dicionário de arquivos
        'dist/index.html': 'src/index.html',     // 'destino': 'source'
        'dist/contato.html': 'src/contato.html'
      }
    },
    dev: {                                       // Outro alvo
      files: {
        'dist/index.html': 'src/index.html',
        'dist/contato.html': 'src/contato.html'
      }
    }
  }
});

grunt.registerTask('default', ['htmlmin']);
```
## Licença

MIT License © [Sindre Sorhus](https://github.com/gruntjs/grunt-contrib-htmlmin/blob/master/LICENSE-MIT)