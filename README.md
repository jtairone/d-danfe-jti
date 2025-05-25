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

***Usando URL da logomarca***


```javascript
const danfe = require('d-danfe-jti');
const logo = 'URL da logomarca da empresa'; // Opcional. Caso não seja informado, o campo ficará vazio. Pode ser passado Buffer.
//Retorna uma promisse tendo utilizar await.
const Danfe = await danfe.fromXML('conteúdo XML', logo);
console.log(await Danfe.toHtml());

```
**Dica:** Recomenda-se utilizar serviços como o [Postimage]('https://postimages.org/') para hospedar sua logomarca e fornecer o URL direto da imagem. 

***Usando um arquivo de logo local***

Sempre passar o caminho relativo, pois será resolvido pelo pacote:
```javascript
const danfe = require('d-danfe-jti');

const logo = './usr/img/logo.png'; // Opcional. Caso não seja informado, o campo ficará vazio. pode ser Buffer.
const Danfe = await danfe.fromXML('conteúdo XML', logo);
console.log(await Danfe.toHtml());
```

***Dica:*** Caso precise acessar um arquivo localizado em subpastas, como o `router.js` na estrutura abaixo, ajuste o caminho relativo para voltar um nível na hierarquia.

Por exemplo, no caso do arquivo `router.js` (localizado em `raiz/api/`) acessando o `logo.png`, o caminho relativo correto seria:
```bash
../usr/img/logo.png
```
***Estrutura de pastas:***
```plaintext Copiar código
raiz/
├── api/
│   ├── functions/
│   │   ├── arquivo.js
│   │   ├── arquivo2.js 
│   └── router.js
├── usr/
│   └── img/
│       └── logo.png
└── server.js
```
### Explicação:
1. O arquivo `router.js` está localizado em `raiz/api/`.
2. Para acessar `logo.png` que está em `raiz/usr/img`, é necessário sair da pasta api usando `../` e então especificar o caminho `usr/img/logo.png`.

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
