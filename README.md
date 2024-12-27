# d-danfe-jti

Este projeto é um fork de [d-danfe]('https://www.npmjs.com/package/d-danfe') com melhorias para suportar links de logos e ajuste automático do tamanho da imagem para um tamanho predefinido.
#
Visualizador de DANFE (Documento Auxiliar Da Nota Fiscal Eletrônica) em HTML.

## Preparação

### Pré-requisitos

NodeJS 8.x ou superior

### Instalação

```
npm i d-danfe-jti
```

### Exemplos de Uso

Este pacote suporta tanto URLs de logos quanto arquivos locais.
```javascript
const logo = 'URL da logomarca da empresa'; // Opcional. Caso não seja informado, o campo ficará vazio.
const danfe = require('d-danfe', logo);
const Danfe = danfe.fromXML('conteúdo XML');
console.log(Danfe.toHtml());

```
**Dica:** Recomenda-se utilizar serviços como o [Postimage]('https://postimages.org/') para hospedar sua logomarca e fornecer o URL direto da imagem. 

Passando um arquivo de logo local, sempre passar o caminho absoluto
```javascript
const path = require('path')

const logo = path.join(__dirname, '/usr/img.logo.png'); // Opcional. Caso não seja informado, o campo ficará vazio.
const danfe = require('d-danfe', logo);
const Danfe = danfe.fromXML('conteúdo XML');
console.log(Danfe.toHtml());

```

## Especificações

### Funções

* Gerar representação do DANFE em HTML a partir de um arquivo XML.
* Formatação somente no formato retrato.
* Contagem do número de folhas geradas.

### Limitações

* **Conversão para outros formatos (ex.: PDF ou imagens)**: Utilize ferramentas externas, como  [Puppeteer](https://github.com/puppeteer/puppeteer/tree/main).
* **Validação dos campos da NFE:** Não há validação dos valores nos campos.
* **TODO:** Não possui geração do código de barras.
* **TODO:** Não possui quebra do número de folhas de acordo com a quantidade de itens.
* **TODO:** Não possui a representação em formato paisagem.

## Testes

```bash
npm run test
```
## Licença

Este projeto é licenciado sob os termos da [Licença MIT.](https://github.com/djalmaoliveira/djf-danfe/blob/master/LICENSE)
