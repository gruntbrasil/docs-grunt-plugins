# grunt-scp

Este plugin realiza a cópia de arquivos para um servidor remoto.

## Iniciando

Este plugin requer a versão ~0.4.0 do Grunt.

**Instalação:** `npm install grunt-scp`

**Inicialização:** `grunt.loadNpmTasks('grunt-scp');`


## A tarefa "scp"

### Visão Geral

No seu arquivo `Gruntfile.js`, adicione uma seção nomeada como `scp` a ser passada no método `.initConfig()`.

Confira o exemplo:

```js
grunt.initConfig({
  pkg: grunt.file.readJSON('package.json'),

  scp: {
    options: {
        host: 'localhost',
        username: 'username',
        password: 'password'
    },
    seu_alvo: {
        files: [{
            cwd: 'directory',
            src: '**/*',
            filter: 'isFile',
            // path on the server
            dest: '/home/username/static/<%= pkg.name %>/<%= pkg.version %>'
        }]
    },
  },
})
```

### Opções

#### options.host

**Tipo:** *String* | **Valor padrão:** *localhost*

O *host* do servidor.

#### options.port

**Tipo:** *Number* | **Valor padrão:** *22*

A porta SSH no servidor.

#### options.username

**Tipo:** *String*

O usuário no servidor remoto.

#### options.password

**Tipo:** *String*

A senha do usuário no servidor remoto.

#### options.log

**Tipo:** *Function*

---

### Opções avançadas

#### options.hostHash

**Tipo:** *String* | **Valores:** *'md5'* ou *'sha1'*

A chave do *host* se comporta como um *hash*, utilizando um dos valores descritos acima e passados na função *hostVerifier*.

#### options.hostVerifier

**Tipo:** *Function* | **Valor padrão:** *'none'*

Função para verificação de *hashes*.  Retorna *true* para continuar com a conexão, *false* pare rejeitar e desconectar.

#### options.agent

**Tipo:** *String* | **Valor padrão:** *'none'*

Caminho para o agente de autenticação SSH que permite utilizar um método de acesso confiável.

**Usuários Windows:** definir como "pageant" para autenticação com Pageant.

#### options.privateKey

**Tipo:** *Mixed* | **Valor padrão:** *'none'*

Chave privada para autenticação do usuário (baseado no formato OpenSSH).

#### options.publicKey

**Tipo:** *Mixed* | **Valor padrão:** *'none'*

Chave pública para autenticação do usuário (baseado no formato OpenSSH). Se uma chave pública não estiver definida, será utilizada uma chave privada.

#### options.passphrase

**Tipo:** *String* | **Valor padrão:** *'none'*

Palavra-passe para descriptografar uma chave privada anteriormente criptografada.

Mais informações: [https://github.com/mscdex/ssh2#connection-methods](https://github.com/mscdex/ssh2#connection-methods)

