# grunt-processhtml

> Processa os arquivos HTML no momento do *build* a fim de modificá-los de acordo com o ambiente de produção.


## Iniciando

Este plugin necessita do Grunt `~0.4.0`

**Instalação:** `npm install grunt-processhtml --save-dev`

**Inicialização:** `grunt.loadNpmTasks('grunt-processhtml');`

## A tarefa "processhtml"

Processe arquivos `html` com comentários especiais:

```html
<!-- build:<tipo>[:alvo] [valor] -->
...
<!-- /build -->
```

##### tipo - *obrigatório*

Tipos: `js`, `css`, `remove`, `template` ou `include`. Ou qualquer tipo de atributo HTML que seja escrito da seguinte forma: `[href]`, `[src]`, etc.

##### alvo - *opcional*

Se o alvo for o nome da sua tarefa grunt, por exemplo: `dist`. Há suporte para todos os **tipos**, então você pode especificar o alvo se necessário.

##### valor
Necessário para os **tipos**: `js`, `css`, `include` e `[attr]`.

Opcional para os tipos: `remove`, `template`.

Pode ser um nome de arquivo (ex.: `script.min.js`) ou um caminho, caso seja um atributo (ex.: `[src]`) e você queira deixar o nome original do arquivo, apenas modificando o seu caminho.

### Exemplos Simples

##### `build:js[:alvo] <valor>`

Substitui diversas tags `script` em uma somente.

- `[:alvo]` alvo opcional para o *build*
- `<valor>` valor necessário: o caminho para o arquivo

```html
<!-- build:js app.min.js -->
<script src="my/lib/path/lib.js"></script>
<script src="my/deep/development/path/script.js"></script>
<!-- /build -->

<!-- modificado para -->
<script src="app.min.js"></script>
```

##### `build:css[:alvo] <valor>`

Substitui diversos links `stylesheets` em um somente.

- `[:alvo]` alvo opcional para o *build*
- `<valor>` valor necessário: o caminho para o arquivo

```html
<!-- build:css style.min.css -->
<link rel="stylesheet" href="path/to/normalize.css">
<link rel="stylesheet" href="path/to/main.css">
<!-- /build -->

<!-- modificado para -->
<link rel="stylesheet" href="style.min.css">
```

##### `build:<[attr]>[:alvo] <valor>`

Modifica o valor de um atributo. Na maioria dos casos utilizar `[src]` e `[href]` será o suficiente, mas funciona com qualquer atributo HTML.

- `<[attr]>` atributo HTML necessário, por exemplo: `[src]`, `[href]`.
- `[:alvo]` alvo opcional para o *build*
- `<valor>` valor necessário: o caminho **ou** caminho com o nome do arquivo

```html
<!-- Utilizando somente o caminho, o nome original será mantido -->

<!-- build:[src] js/ -->
<script src="my/lib/path/lib.js"></script>
<script src="my/deep/development/path/script.js"></script>
<!-- /build -->

<!-- modificado o caminho do atributo src -->
<script src="js/lib.js"></script>
<script src="js/script.js"></script>

<!-- build:[href] img/ -->
<link rel="apple-touch-icon-precomposed" href="skins/demo/img/icon.png">
<link rel="apple-touch-icon-precomposed" href="skins/demo/img/icon-72x72.png" sizes="72x72">
<!-- /build -->

<!-- modificado o caminho do atributo href -->
<link rel="apple-touch-icon-precomposed" href="img/icon.png">
<link rel="apple-touch-icon-precomposed" href="img/icon-72x72.png" sizes="72x72">

<!-- build:[class]:dist production -->
<html class="debug_mode">
<!-- /build -->

<!-- isso vai modificar a classe para 'production' somente quando houver um build do 'dist' -->
<html class="production">

```

##### `build:include[:alvo] <valor>`

Inclui um arquivo externo.

- `[:alvo]` alvo opcional para o *build*
- `<valor>` valor necessário: o caminho com o nome do arquivo

```html
<!-- build:include header.html -->
Isto será substituído com o conteúdo de header.html
<!-- /build -->

<!-- build:include:dev dev/content.html -->
Isto será substituído com o conteúdo de dev/content.html
<!-- /build -->

<!-- build:include:dist dist/content.html -->
Isto será substituído com o conteúdo de dist/content.html
<!-- /build -->
```

##### `build:template[:alvo]`

Processa um bloco de template com os metadados dentro de [options.data](#optionsdata).

- `[:alvo]` alvo opcional para o *build*


```html
<!-- build:template
<p>Olá, <%= nome %></p>
/build -->

<!--
note que o bloco do template está comentado para manter 
o bom funcionamento e evitar que o arquivo html quebre
-->
```

##### `build:remove[:target]`

Remove um bloco.

- `[:alvo]` alvo opcional para o *build*

```html
<!-- build:remove -->
<p>Isto será removido assim que qualquer alvo do "processhtml" for concluído</p>
<!-- /build -->

<!-- build:remove:dist -->
<p>Mas, este será somente removido quando o alvo "processhtml:dist" for executado</p>
<!-- /build -->
```

### Visão Geral

No `Gruntfile.js` do seu projeto, adicione uma seção chamada `processhtml` dentro do método `initConfig()`.

```js
grunt.initConfig({
  processhtml: {
    options: {
      // defina aqui as opções referente a esta tarefa
    },
    seu_alvo: {
      // defina aqui a lista de arquivos e/ou opções para este alvo
    },
  },
})
```

### Opções

#### options.process
Tipo: `Boolean`
Valor padrão: `false`

Processa o `html` inteiro através do `grunt.template.process`, onde um objeto padrão com o alvo a ser compilado será passado para o template no formato `{environment: target}` sendo *environment* o alvo do *build* na tarefa do grunt.

*Nota importante: a opção `process` não é necessária caso você não queira processar o arquivo html completamente. Veja o exemplo abaixo onde é possível processar blocos de templates.*

Se você não quiser processar o arquivo inteiro como um template, ele será compilado depois que os blocos de templates dentro dele forem compilados (caso exista algum).

#### options.data
Tipo: `Object`
Valor padrão: `{environment: target}`

Um objeto `data` que será passado para o arquivo `html` e usado para compilar todos os blocos de template e o arquivo inteiro caso `process` esteja definido como `true`. Se um objeto customizado for passado assim como `data`, este será "mesclado" ao objeto padrão a fim de manter a chave `environment` intacta.

#### options.templateSettings
Tipo: `Object`
Valor padrão: `null` (usará o delimitador padrão do grunt `<%` e `%>`)

A opção `templateSettings` define uma sintaxe customizada para estes delimitadores, de acordo com os valores inseridos em `opener` e `closer`.

```javascript
templateSettings: {
  opener: '{{',
  closer: '}}'
}
```

### Exemplos de Uso

#### Opções Padrão

Defina a tarefa no seu arquivo `Gruntfile.js` que vai processar o arquivo `index.html` e salvar uma saída em: `dest/index.html`.

```js
grunt.initConfig({
  processhtml: {
    options: {
      data: {
        message: 'Olá, mundo!'
      }
    },
    dist: {
      files: {
        'dest/index.html': ['index.html']
      }
    }
  }
});
```

#### O que será processado?

De acordo com a configuração da tarefa anterior, podemos dizer que o `index.html` se parece com isso:

```html
<!doctype html>
<title>title</title>

<!-- build:[href] img/ -->
<link rel="apple-touch-icon-precomposed" href="my/theme/img/apple-touch-icon-precomposed.png">
<link rel="apple-touch-icon-precomposed" href="my/theme/img/apple-touch-icon-72x72-precomposed.png" sizes="72x72">
<!-- /build -->

<!-- build:css style.min.css -->
<link rel="stylesheet" href="normalize.css">
<link rel="stylesheet" href="main.css">
<!-- /build -->

<!-- build:js app.min.js -->
<script src="js/libs/require.js" data-main="js/config.js"></script>
<!-- /build -->

<!-- build:include header.html -->
This will be replaced by the content of header.html
<!-- /build -->

<!-- build:template
<p><%= message %></p>
/build -->

<!-- build:remove -->
<p>This is the html file without being processed</p>
<!-- /build -->
```

Após processar este arquivo, a sua saída será:

```html
<!doctype html>
<title>title</title>

<link rel="apple-touch-icon-precomposed" href="img/apple-touch-icon-precomposed.png">
<link rel="apple-touch-icon-precomposed" href="img/apple-touch-icon-72x72-precomposed.png" sizes="72x72">

<link rel="stylesheet" href="style.min.css">

<script src="app.min.js"></script>

<h1>Content from header.html</h1>

<p>Hello world!</p>
```

#### Exemplo avançado

Neste exemplo, existem múltiplos alvos que podemos processar no arquivo `html` dependendo de qual alvo será executado.

```js
grunt.initConfig({
  processhtml: {
    dev: {
      options: {
        data: {
          message: 'Este é um ambiente de desenvolvimento!'
        }
      },
      files: {
        'dev/index.html': ['index.html']
      }
    },
    dist: {
      options: {
        process: true
        data: {
          title: 'Meu aplicativo',
          message: 'Este é um ambiente de produção!'
        }
      },
      files: {
        'dest/index.html': ['index.html']
      }
    },
    custom: {
      options: {
        templateSettings: {
          opener: '{{',
          closer: '}}'
        },
        data: {
          message: 'Isto possui um delimitador customizado'
        }
      },
      files: {
        'custom/custom.html': ['custom.html']
      }
    }
  }
});
```

O `index.html` que será processado (o arquivo `custom.html` está logo em seguida):

```html
<!doctype html>
<!-- perceba que não existe um comentário especial aqui, já que 'process' está definido como 'true'. -->
<title><%= title %></title>

<!-- build:css style.min.css -->
<link rel="stylesheet" href="normalize.css">
<link rel="stylesheet" href="main.css">
<!-- /build -->

<!-- build:template
<p><%= message %></p>
/build -->

<!-- build:remove -->
<p>Este é o arquivo html sem ser processado</p>
<!-- /build -->

<!-- build:remove:dist -->
<script src="js/libs/require.js" data-main="js/config.js"></script>
<!-- /build -->

<!-- build:template
<% if (environment === 'dev') { %>
<script src="app.js"></script>
<% } else { %>
<script src="app.min.js"></script>
<% } %>
/build -->
```

O arquivo `custom.html` a ser processado:
```html
<!doctype html>
<html>
  <head>
    <title>Exemplo para os delimitadores customizados</title>
  </head>

  <body>
    <!-- build:template
    {{= message }}
    /build -->
  </body>
</html>
```

