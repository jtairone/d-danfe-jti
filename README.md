# d-danfe-jti

Este projeto é um fork de [d-danfe]('https://www.npmjs.com/package/d-danfe') fiz somente umas melhorias para poder enviar o link do logo e ajuste de tamanho da imagem automaticamente para um tamanho predefinido
#
Visualizador de DANFE (Documento Auxiliar Da Nota Fiscal Eletrônica) em HTML.

## Preparação

### Pré-requisitos

NodeJS 8.x

### Instalação

```
npm i d-danfe-jti
```

### Exemplos

Tanto pode passar a URL do logo quanto informar um arquivo local.
```
const logo = 'URL logomarca empresa'
//opcional passar o logo se não enviar fica vazio
const danfe = require('d-danfe', logo)
const Danfe = danfe.fromXML('conteudo XML')
console.log(Danfe.toHtml())
```
* recomendo utilizar o [Postimage](https://postimages.org/) publicar online a imagem e passar o url direta do logo 

## Especificações

### Funções

* Criar representação do DANFE em HTML baseado somente em um arquivo XML existente.
* Criar a representação somente no formato retrato.
* Possui contagem do número de folhas.

### Limitações

* Não converte para outros formatos como pdf e imagens (basta usar um conversor externo, ex.: [puppeteer](https://github.com/puppeteer/puppeteer/tree/main)).
* Não valida os valores dos campos da NFE.
* (TODO) Não possui geração do código de barras.
* (TODO) Não possui quebra do número de folhas de acordo com a quantidade de itens.
* (TODO) Não possui a representação em formato paisagem.

## Testes

```
npm run test
```
## Licença

[MIT](https://github.com/djalmaoliveira/djf-danfe/blob/master/LICENSE)
