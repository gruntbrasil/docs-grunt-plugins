# grunt-cli [![Build Status](https://secure.travis-ci.org/gruntjs/grunt-cli.png?branch=master)](http://travis-ci.org/gruntjs/grunt-cli)

> Documentação oficial: [https://github.com/gruntjs/grunt-cli](https://github.com/gruntjs/grunt-cli)

Instale globalmente e poderá acessar os comandos do 'grunt' em qualquer local do seu sistema.

```shell
npm install -g grunt-cli
```

**Nota:** A função do comando `grunt` é carregar e executar a versão do Grunt que você instalou localmente no seu projeto, não importa qual seja a versão. Iniciando pelo Grunt v0.4, você nunca deve instalar o Grunt globalmente. Para mais informações, [por favor leia](http://blog.nodejs.org/2011/03/23/npm-1-0-global-vs-local-installation).
 
Leia o [Guia de Introdução](http://gruntjs.com/getting-started) para mais informações.

## Preenchimento automatico do Shell 
Para habilitar o preenchimento automatico para o Grunt, adicione uma dessas linhas ao seu arquivo `~/.bashrc` ou `~/.zshrc`.

```bash
# Bash, ~/.bashrc
eval "$(grunt --completion=bash)"
```

```bash
# Zsh, ~/.zshrc
eval "$(grunt --completion=zsh)"
```

## Instalando o grunt-cli localmente
Se você achar melhor o método "Idiomatic Node.js" para iniciar um projeto (`npm install && npm test`) e instalar o grunt-cli localmente com o `npm install grunt-cli --save-dev`. Adicione um script no seu `package.json` para rodar o comando associado do Grunt: `"scripts": { "test": "grunt test" } `. Agora o `npm test` vai usar o `./node_modules/.bin/grunt` local para executar seus comandos.

Para ler mais sobre os comandos do npm, visite a documentação: [https://npmjs.org/doc/misc/npm-scripts.html](https://npmjs.org/doc/misc/npm-scripts.html).
