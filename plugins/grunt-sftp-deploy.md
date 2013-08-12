# grunt-sftp-deploy

> Documentação oficial: [https://npmjs.org/package/grunt-sftp-deploy](https://npmjs.org/package/grunt-sftp-deploy)

## Sobre

Esta é uma tarefa do grunt para deploy de arquivos, utlizando o protocolo SFTP. É, sobretudo, uma cópia do [grunt-ftp-deploy](https://github.com/zonak/grunt-ftp-deploy), mas utiliza o módulo [SSH2](https://github.com/mscdex/ssh2) para fornecer acesso SFTP em vez de [JSFTP](https://github.com/sergi/jsftp).


Nos dias de hoje, o **Git** não é apenas a nossa ferramenta de gerenciamento de código no estilo *goto*, mas em muitos casos a nossa ferramenta para deploy também. Mas, há muitos casos em que o **Git** não se encaixa para deploy:


* permite apenas deploy para servidores com acesso SFTP
* o código de produção é resultado do processo de construção na produção de arquivos que não necessariamente acompanhamos com **Git**

É por isso que uma tarefa como está seria muito útil.

Para fins de simplicidade, esta tarefa evita apagar qualquer arquivo e não faz qualquer tipo de comparação entre eles, seja por data ou tamanho. Ele simplesmente transfere todos os arquivos (e estrutura de diretórios) do seu ambiente de desenvolvimento local para o seu servidor.


## Uso

Para utilizar esta tarefa, será preciso incluir a configuração a seguir no seu arquivo **Gruntfile**:

    'sftp-deploy': {
      build: {
        auth: {
          host: 'server.com',
          port: 22,
          authKey: 'key1'
        },
        src: '/caminho/para/diretorio/local',
        dest: '/caminnho/para/diretorio/remoto',
        exclusions: ['/caminho/diretorio/local/**/.DS_Store', '/caminho/diretorio/local/**/Thumbs.db', 'dist/tmp'],
        server_sep: '/'
      }
    }

e carregar a tarefa:

    grunt.loadNpmTasks('grunt-sftp-deploy');


### Opções
Os parâmetros para configuração, são:

* **host** - o nome ou IP do seu servidor paa deploy
* **port** - a porta em que o SFTP estará rodando
* **authKey** - a chave pública para veriricar as sua credenciais
* **src** - o local onde os seus arquivos se encontram na sua máquina
* **dest** - o caminho do servidor para onde os arquivos serão enviados
* **exclusions** - um parâmetro opcional que permite a exclusão de arquivos e diretórios
* **server_sep** - um parâmetro opcional que permite definir um separador caso esteja trabalhando em ambiente diferentes. Útil, se você fizer o deploy do Windows para Unix.

## Parâmetros de autenticação

As referências de usuários, senhas e chaves privadas são armazenados como objetos JSON em um arquivo chamado `.ftppass`. Este arquivo, segue o seguinte padrão:

    {
      "key1": {
        "username": "username1",
        "password": "password1"
      },
      "key2": {
        "username": "username2",
        "password": "password2"
      },
      "privateKey": {
        "username": "username"
      },
      "privateKeyEncrypted": {
        "username": "username",
        "passphrase": "passphrase1"
      },
      "privateKeyCustom": {
        "username": "username",
        "passphrase": "passphrase1",
        "keyLocation": "/full/path/to/key"
      }
    }

Caso, `keyLocation` não esteja especificado, `grunt-sftp-deploy` fará uma busca por chaves em `~/.ssh/id_dsa` e `/.ssh/id_rsa`.

Você pode fornecer senhas para chaves criptografadas com o atributo `passphrase`.

Dessa forma, podemos salvar quntas combinações de usuário / senha quisermos e procurá-los pelo valor `authKey` definido no arquivo de configuração do grunt onde o resto dos parâmetros-alvo estão definidos.


## Dependências

Esta tarefa foi construída, aproveitando a grande obra de Brian White e seu módulo [ssh2](https://github.com/mscdex/ssh2).