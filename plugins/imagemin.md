
# ImageMin - Otimização de Imagens

> Documentação para Referência: [https://www.npmjs.org/package/grunt-contrib-imagemin](https://www.npmjs.org/package/grunt-contrib-imagemin)


## Sobre

O **grunt-contrib-imagemin** é um plugin muito indicado para otimizar as imagens de um projeto que você quer criar. Para quem não sabe, otimização é uma técnica usada no desenvolvimento que torna o site mais legível aos mecanismos de busca. Então, esse plugin faz com que as imagens no formato PNG, GIF e JPEG sejam otimizadas, deixando até um pouco mais leve.

## Como aplicá-lo?

> OTIMIZE SUAS IMAGENS

Para usar o **grunt-contrib-imagemin** em seu projeto, é preciso digitar o script abaixo via linha de comando.

`npm install grunt-contrib-imagemin`

OBS: Esta tarefa exige que você tenha NODE instalado para baixar os pacotes NPM's.

## Usando o Plugin

No arquivo **Gruntfile** do seu projeto, adicione uma seção nomeada como **imagemin** para que os objetos sejam passados dentro do método grunt.initConfig(). Confira um exemplo abaixo.

> Configuração

	var mozjpeg = require('imagemin-mozjpeg'); // Variavel recebe uma dependência para uso local

	grunt.initConfig({
	  imagemin: {                          // Buscas imagens específicas
	    static: {                          
	      options: {                       
	        optimizationLevel: 3,
	        use: [mozjpeg()]
	      },
	      files: {                         
	        'dist/img.png': 'src/img.png', 
	        'dist/img.jpg': 'src/img.jpg',
	        'dist/img.gif': 'src/img.gif'
	      }
	    },
	    dynamic: {                         // Busca as imagens dinamicas
	      files: [{
	        expand: true,                  
	        cwd: 'src/',                   
	        src: ['**/*.{png,jpg,gif}'],   
	        dest: 'dist/'                  
	      }]
	    }
	  }
	});

	grunt.loadNpmTasks('grunt-contrib-imagemin');
	grunt.registerTask('default', ['imagemin']);


## Site Oficial

* [GruntJS](http://gruntjs.com/)
* [Repositório Oficial](https://www.npmjs.org/package/grunt-contrib-imagemin)