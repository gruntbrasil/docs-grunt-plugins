# load-grunt-tasks [![Build Status](https://secure.travis-ci.org/sindresorhus/load-grunt-tasks.png?branch=master)](http://travis-ci.org/sindresorhus/load-grunt-tasks)


## Sobre

Este é um plugin que carrega múltiplas tarefas do Grunt usando *globbing patterns*. Normalmente você teria que carregar cada tarefa, uma por uma, o que pode se tornar complicado. Este módulo irá ler o `devDependencies` no seu `package.json` e carregar as tarefas que correspondem ao *pattern*.


#### Antes

```js
grunt.loadNpmTasks('grunt-shell');
grunt.loadNpmTasks('grunt-sass');
grunt.loadNpmTasks('grunt-recess');
grunt.loadNpmTasks('grunt-sizediff');
grunt.loadNpmTasks('grunt-svgmin');
grunt.loadNpmTasks('grunt-styl');
grunt.loadNpmTasks('grunt-php');
grunt.loadNpmTasks('grunt-eslint');
grunt.loadNpmTasks('grunt-concurrent');
grunt.loadNpmTasks('grunt-bower-requirejs');
```

#### Depois

```js
require('load-grunt-tasks')(grunt);
```


## Instalação

Instale com [npm](https://npmjs.org/package/load-grunt-tasks): `npm install --save load-grunt-tasks`


## Exemplo

```js
// Gruntfile.js
module.exports = function (grunt) {
	// carregar todas as tarefas correspondentes ao pattern `grunt-*`
	require('load-grunt-tasks')(grunt);

	grunt.initConfig();
	grunt.registerTask('default', []);
}
```

Por padrão `grunt-*` será usado como [globbing pattern](https://github.com/isaacs/minimatch).

Opcionalmente, você pode especificar um pattern ou um array de patterns:

```js
require('load-grunt-tasks')(grunt, 'grunt-shell');
```

```js
require('load-grunt-tasks')(grunt, 'grunt-contrib-*');
```

```js
require('load-grunt-tasks')(grunt, ['grunt-contrib-*', 'grunt-shell']);
```

Você também tem a opção de especificar o package.json como um objeto se ele não está na mesma pasta que o Gruntfile:

```js
require('load-grunt-tasks')(grunt, 'grunt-shell', require('../package'));
```


## Licença

MIT License • © [Sindre Sorhus](http://sindresorhus.com)
