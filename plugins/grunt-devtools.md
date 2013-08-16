# Grunt Dev Tools

> Documentação oficial: [https://github.com/vladikoff/grunt-devtools](https://github.com/vladikoff/grunt-devtools)

## Sobre

O grunt-devtools é um plugin para ser utilizado juntamente com uma extensão do Chrome Dev Tools. Este plugin permite que suas tarefas fiquem acesíveis no Chrome Dev Tools.

## Iniciando

1. Faça o download da extensão do [Grunt Dev Tools](https://chrome.google.com/webstore/detail/grunt-devtools/fbiodiodggnlakggeeckkjccjhhjndnb?hl=en) na Chrome Web Store.
2. Execute o comando `npm install grunt-devtools` no diretório do seu projeto
3. Adicione `grunt.loadNpmTasks('grunt-devtools');` no seu arquivo `Gruntfile.js`
4. Execute a tarefa com: `grunt devtools`
5. Abra o **Chrome Dev Tools** e clique na aba do Grunt. Pronto! Suas tarefas estarão acessíveis através do Chrome Dev Tools a partir de agora.

## Atualizando

* A atualização de uma extensão no Chrome ocorre automaticamente, mas você pode forçar uma atualização utilizando `chrome://extensions`

![https://github-camo.global.ssl.fastly.net/475613ff349f1098799f7495f976acae2af61dde/687474703a2f2f763134642e636f6d2f692f353133636262386132306166342e706e67](https://github-camo.global.ssl.fastly.net/475613ff349f1098799f7495f976acae2af61dde/687474703a2f2f763134642e636f6d2f692f353133636262386132306166342e706e67)

* A atualização do plugin pode ser feita com `npm install grunt-devtools` (atualização automática estará disponível em breve)
* As versões, tanto do plugin quanto da extensão devem sempre combinar (`0.1.0.1` no Chrome é `0.1.0-1` no npm)

![https://github-camo.global.ssl.fastly.net/249c1e84087e40b7d0e37483e7e00ce88d258245/687474703a2f2f763134642e636f6d2f692f353133343535396264623233612e6a7067](https://github-camo.global.ssl.fastly.net/249c1e84087e40b7d0e37483e7e00ce88d258245/687474703a2f2f763134642e636f6d2f692f353133343535396264623233612e6a7067)

## O plugin em ação

![https://github-camo.global.ssl.fastly.net/fe71131fd0be3575fd64f22d8e14be2e1044ef6a/687474703a2f2f763134642e636f6d2f692f353133333934383033643364392e6a7067](https://github-camo.global.ssl.fastly.net/fe71131fd0be3575fd64f22d8e14be2e1044ef6a/687474703a2f2f763134642e636f6d2f692f353133333934383033643364392e6a7067)
![https://github-camo.global.ssl.fastly.net/a29ca457281aeea3886c3d11340fbddde22ac16d/687474703a2f2f763134642e636f6d2f692f353133333933636262376538622e6a7067](https://github-camo.global.ssl.fastly.net/a29ca457281aeea3886c3d11340fbddde22ac16d/687474703a2f2f763134642e636f6d2f692f353133333933636262376538622e6a7067)
![https://github-camo.global.ssl.fastly.net/b91122bc1cbc8b704a700f10a731c02b8bbb20f7/687474703a2f2f763134642e636f6d2f692f353133333934316365623662342e6a7067](https://github-camo.global.ssl.fastly.net/b91122bc1cbc8b704a700f10a731c02b8bbb20f7/687474703a2f2f763134642e636f6d2f692f353133333934316365623662342e6a7067)

## Configuração de Desenvolvimento

### Chrome Extension

* Carregue a extensão descompactada no diretório de extensão.

### Instalação do plugin para Grunt

* Instale o plugin localmente, utilizando o `npm install [folder]/grunt-plugin`
* Add grunt.loadNpmTasks('grunt-devtools'); to your Gruntfile
* run grunt devtools


## Sugestões

* Caso tenha algum problema, faça uma [atualização](grunt-devtools.md#atualizando) antes.
* Confira o [wiki](https://github.com/vladikoff/grunt-devtools/wiki) do projeto.
* Se o problema persistir, [reporte](https://github.com/vladikoff/grunt-devtools/issues) o mesmo ou peça ajuda no canal `#grunt` do `freenode`.

## Limitações atuais

* A extensão vai funcionar por até cinco instâncias do `grunt devtools` de uma vez (isso significa que se você gosta de trabalhar em mais de cinco projetos de cada vez, você terá que desligar a tarefa).
* As tarefas de fundo desaparecem quando finalizadas.

## Licença

MIT License • © Vlad Filippov
