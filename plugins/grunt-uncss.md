# grunt-uncss

> Uma tarefa do Grunt para remover estilos CSS que não serão utilizados no projeto. Funciona através de arquivos múltiplos.

*Note: este projeto encontra-se em uma versão prévia e inicial de desenvolvimento.*

## Preview

Escolhendo um projeto de múltiplas páginas que utiliza o Bootstrap com **120KB** de CSS e reduzindo-o para **11KB**.

![](http://i.imgur.com/uhWMALH.gif)

## Iniciando

Este plugin necessita do Grunt `~0.4.0`

**Instalação:** `npm install grunt-uncss --save-dev`

**Inicialização:** `grunt.loadNpmTasks('grunt-uncss');`

## A tarefa

Execute esta tarefa com o comando: `grunt uncss`

Os alvos, arquivos e opções desta tarefa devem ser especificados de acordo com o guia de [configuração de tarefas](http://gruntjs.com/configuring-tasks) do Grunt.

Remove o CSS não utilizado no projeto com o [uncss](https://github.com/giakki/uncss).

### Como usar

Utilize a tarefa `grunt-uncss` especificando o destino (arquivo) do seu CSS a ser gerado. No exemplo abaixo, temos: `dist/css/tidy.css`. 

Especifique os arquivos HTML que terão os seletores vasculhados. Neste caso, temos os arquivos `app/index.html` e `app/about.html` a serem vasculhados.

```shell
uncss: {
  dist: {
    files: {
      'dist/css/tidy.css': ['app/index.html','app/about.html']
      }
    }
},
```

Que você pode utilizar juntamente com um processador, tal como o `processhtml`, para re-escrever a localização da sua folha de estilo utilizando um bloco, como:

```html
<!-- build:css css/tidy.css -->
<link rel="stylesheet" href="css/normalize.css">
<link rel="stylesheet" href="css/main.css">
<link rel="stylesheet" href="css/bootstrap.css">
<!-- /build -->
```

e com algumas configurações, como:

```shell
processhtml: {
  dist: {
    files: {
      'dist/index.html': ['app/index.html'],
      'dist/about.html': ['app/about.html']
    }
  }
}
```

## Opções

### compress

`compress` vai comprimir o seu CSS assim que forem removidos os estilos não utilizados no seu projeto.

### ignore

`ignore` vai ignorar determinados seletores no momento em que o processo de análise estiver sendo executado. Por exemplo:

```javascript
ignore: ['#added_at_runtime', '.created_by_jQuery']
```

### Exemplo de uso

```shell
// Remove CSS não utilizado atraés de múltiplos arquivos
uncss: {
  dist: {
    files: {
      'dist/css/tidy.css': ['app/index.html','app/about.html']
      }
    }
},
```

```shell
// Remove CSS não utilizado atraés de múltiplos arquivos, com o arquivo de saída comprimido
uncss: {
  dist: {
    files: {
      'dist/css/tidy.css': ['app/index.html','app/about.html']
      }
    },
    options: {
      compress:true
    }
}
```

```shell
// Remove CSS não utilizado atraés de múltiplos arquivos, ignorando seletores específicos
uncss: {
  dist: {
    files: {
      'dist/css/tidy.css': ['app/index.html','app/about.html']
      }
    },
    options: {
      ignore: ['#added_at_runtime', '.created_by_jQuery']
    }
}
```

### Projeto de teste

Existe um projeto de teste dentro do diretório `app` onde pode ser feito o um *build* executando `npm install && grunt`. Disponível também uma tarefa chamada `grunt compare_size` que exibe um comparativo do tamanho (KB) dos arquivos antes e depois:

![](http://i.imgur.com/bUseCPh.png)


## O problema

Bibliotecas UI como o Bootstrap, TopCoat e outras ajudam muito na produtividade. Entretanto, muitos desenvolvedores utilizam menos de 10% do CSS contídos neles (quando optam pela compilação completa, o que a maioria faz). Como resultado, eles podem acabar com folhas de estilo bastante "inchadas", o que pode aumentar significativamente o tempo de carregamento da página e afetar o desempenho do projeto.

O `grunt-uncss` é uma tentativa para ajudar na geração de um arquivo CSS contendo apenas os estilos usado em seu projeto, com base em testes de seleção.


## Pesquisa e soluções alternativas

No passado, houveram muitos esforços para solucionar o problema em encontrar o CSS não utilizado. A Opera criou o [ucss](https://github.com/operasoftware/ucss), @aanand criou o [deadweight](https://github.com/aanand/deadweight) e foram criadas uma série de soluções do lado cliente também, como: [Helium-CSS](https://github.com/geuis/helium-css), [CSSESS](https://github.com/driverdan/cssess) e o [mincss](http://www.peterbe.com/plog/mincss).

Infelizmente, a maioria destas soluções não gera o que você realmente espera - uma compilação enxuta do seu CSS contendo apenas o que você utilizou no seu projeto. Foi aí que constatei um projeto mais recente chamado [uncss](https://github.com/giakki/uncss) que tentou solucionar isto. Eu me propus a compartilhar alguns dos problemas que precisávamos resolver neste espaço com o desenvolvedor do projeto e construí uma tarefa para o Grunt, a fim de  permitir o uso do mesmo mais facilmente.

O meu "Muito obrigado!" para Giacomo Martino por sua ajuda com o módulo Node que esta tarefa usa.


## Limitações

Atualmente, o `uncss` não pode ser executado com PhantomJS, mas haverá suporte para isso em breve. Isso vai permitir a captura correta de estilos injetados dinamicamente nas páginas do projeto.

Por favor, note que o *parser* para CSS utilizado no módulo `uncss` disponível atualmente não é capaz de trabalhar com seletores complexos. 

Por exemplo: `[data-section=''] > section > [data-section-title] a`. 

Significa que no momento do *build* uma excessão possa ser lançada, como: `TypeError: Cannot convert undefined or null to object`. Neste caso, considere mover este seletor para uma folha de estilo separada e que não será afetada pela tarefa do `grunt uncss`.

Estamos buscando ativamente em como melhorar o *parser* utilizado no CSS e avisaremos assim que encontrarmos uma solução para este problema.

## Licença

(C) Addy Osmani 2013, lançado através da licença MIT.

