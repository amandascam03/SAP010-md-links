# Markdown Links

## Índice

* [1. Resumo do projeto](#1-resumo-do-projeto)
* [2. Como instalar o módulo](#2-como-instalar-o-módulo)
* [3. Informações da aplicação](#3-informações-da-aplicação)
* [4. Fluxograma](#4-fluxograma)
* [5. Testes](#5-testes)
* [6. Tecnologias utilizadas](#6-tecnologias-utilizadas)
* [7. Contato](#7-contato)

***

## 1. Resumo do projeto

Markdown é uma linguagem de marcação muito popular entre os programadores. É usada em muitas plataformas que manipulam texto (GitHub, fórum, blogs e etc) e é muito comum encontrar arquivos com este formato em qualquer repositório (começando pelo tradicional README.md).

Os arquivos `Markdown` normalmente contém _links_ que podem estar
quebrados, ou que já não são válidos, prejudicando muito o valor da
informação que está ali.

O objetivo desta aplicação foi desenvolver uma ferramenta de linha de comando (CLI) que lê e analisa arquivos no formato
`Markdown`, para verificar os arquivos que contenham links e mostrar algumas estatísticas para obter informações relevantes desses links. A biblioteca tem como objetivo de ser utilizada por linha de comando, porém também pode ser importado com `require` para ser utilizado em outros códigos. A biblioteca e script executável foram implementados em JavaScript para serem executadas com Node.JS.

## 2. Como instalar o módulo

**Utilize o seguinte comando no terminal:**

```sh
 $ npm i md-links-mnds
```

`Verifique se você contém arquivos markdown locais para a execução.`

*OBS: Os arquivos markdown válidos contém as seguintes extensões: '.md', '.mkd', '.mdwn', '.mdown', '.mdtxt', '.mdtext', '.markdown', '.text'.*

## 3. Informações da aplicação:

### 1) JavaScript API

O módulo deve ser **importado** em outros scripts Node.js e oferece a
seguinte interface:

#### `mdLinks(path, options)`

##### Argumentos

* `path`: Rota ao arquivo ou diretório.
* `options`: Um objeto com a seguinte propriedade:
  - `validate`: Um booleano que determina se deseja validar os links
    encontrados.
  - `stats`: Booleano que determina se deseja obter um output
    com informações estatísticas gerais.

##### Valor de retorno

A função **retorna uma promessa** (`Promise`) que
**resolve um array** de
objetos, onde cada objeto representa um link, contendo as seguintes
propriedades:

Com `validate:false` :

* `href`: URL encontrada.
* `text`: Texto que irá aparecer dentro de um link (`<a>`).
* `file`: Rota do arquivo onde foi encontrado o link.

Com `validate:true` :

* `href`: URL encontrada.
* `text`: Texto que aparecía dentro del link (`<a>`).
* `file`: Ruta del archivo donde se encontró el link.
* `status`: Código de resposta HTTP.
* `ok`: Mensagem `fail` em caso de falha ou `ok` em caso de sucesso.

#### Exemplo

```sh

const mdLinks = require("md-links");

mdLinks("./some/example.md")
  .then(links => {
    // => [{ href, text, file }, ...]
  })
  .catch(console.error);

mdLinks("./some/example.md", { validate: true })
  .then(links => {
    // => [{ href, text, file, status, ok }, ...]
  })
  .catch(console.error);

mdLinks("./some/dir")
  .then(links => {
    // => [{ href, text, file }, ...]
  })
  .catch(console.error);
```

### 2) CLI (Command Line Interface - Interface de Linha de Comando)

### Executando na CLI

**O executável da aplicação pode ser executado da seguinte maneira, através do terminal:**

```sh
 $ md-links <path-to-file>
  ```

Valor de retorno:

* `href`: URL encontrada.
* `text`: Texto que aparecia dentro do link (`<a>`).
* `file`: Rota do arquivo onde foi encontrado o link.

### Validando os links

**Para obter informações mais precisas do estado atual dos links, você pode adicionar a opção --validate:**

```
$ md-links <path-to-file> --validate
```

Valor de retorno:

* `href`: URL encontrada.
* `text`: Texto que aparecia dentro do link (`<a>`).
* `file`: Rota do arquivo onde foi encontrado o link.
* `status`: Código de resposta HTTP.
* `ok`: Mensagem `fail` em caso de falha ou `ok` em caso de sucesso.

### Verificando links totais e únicos

**Se você precisa verificar a quantidade de links, adicione a opção --stats:**

```sh
$ md-links <path-to-file> --stats
```

Valor de retorno:

* `Total`: Total de links encontrados no arquivo/diretório.
* `Unique`: Quantidade de links únicos (que não se repetem).

### Combinando --stats e --validate

**Utilize essa combinação para verificar, além da quantidade, os links quebrados:**

```sh
$ md-links <path-to-file> --stats --validate
```

Valor de retorno:

* `Total`: Total de links encontrados no arquivo/diretório.
* `Unique`: Quantidade de links únicos (que não se repetem).
* `Broken`: Quantidade de links quebrados.

## 4. Fluxograma

Um fluxograma foi definido antes do código para definir os próximos passos e organização do projeto.

![fluxograma-mdlinks](https://github.com/amandascam03/SAP010-md-links/assets/131325234/6d19e980-39a0-4acc-b194-7f01de902e9a)


## 5. Testes

* Foi utilizado o [Jest](https://jestjs.io/)
  para a execução dos testes unitários.

![testes-unitários](https://github.com/amandascam03/SAP010-md-links/assets/131325234/a06d85fe-bd78-4db5-89d0-12bc1d2e637f)

## 6. Tecnologias utilizadas
<div>
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" width="60px"/>
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" width="60px"/>
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/jest/jest-plain.svg" width="60px"/>
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-plain.svg" width="60px"/>
</div>

## 7. Contato

<div>
  Amanda Araujo <br>
<a href = "mailto:amandascam03@gmail.com"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"></a>
<a href="https://www.linkedin.com/in/amanda-scam03" target="_blank"><img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank"></a>
</div>
