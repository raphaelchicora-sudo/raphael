# Guia do Projeto

Este guia ajuda quem está aprendendo a encontrar rapidamente onde mudar cada parte do site.

## Estrutura Dos Arquivos

`index.html`

Guarda a estrutura e o conteúdo da página principal. Aqui ficam os textos, seções, perguntas do quiz, imagens usadas no HTML, iframe da HQ e rodapé.

`style.css`

Guarda a aparência do site. Aqui ficam cores, tamanhos, espaçamentos, responsividade, cards, botões, menu, carrossel e modo de alto contraste.

`script.js`

Guarda os comportamentos interativos. Aqui ficam menu mobile, acessibilidade, carrossel, curiosidades, quiz, animação ao rolar e cards expansivos.

`HQ/hq.html`

Guarda a história em quadrinhos exibida dentro do iframe da página principal.

## Onde Alterar

### Mudar Cores Do Site

Abra `style.css` e altere apenas o bloco `:root`, no início do arquivo.

Principais variáveis:

- `--color-bg`: fundo principal do site.
- `--color-primary`: verde principal.
- `--color-primary-dark`: verde mais escuro.
- `--color-accent`: dourado usado nos botões e destaques.
- `--color-text`: cor principal dos textos.
- `--color-surface-solid`: fundo dos blocos/cards.

### Mudar Textos Da Página

Abra `index.html` e procure pelo texto que deseja alterar com `Ctrl + F`.

Exemplo: para mudar o título da primeira tela, procure por `<h1>`.

### Mudar Imagens Do Carrossel

Abra `script.js` e procure por:

```js
const carouselItems = [
```

Cada item tem:

- `src`: caminho da imagem.
- `alt`: descrição da imagem para acessibilidade.
- `title`: título exibido abaixo da imagem.
- `description`: texto explicativo.

### Mudar Curiosidades

Abra `script.js` e procure por:

```js
const facts = [
```

Cada frase dentro da lista pode ser trocada ou ampliada.

### Mudar Respostas Do Quiz

As perguntas e alternativas ficam no `index.html`, dentro da seção:

```html
<section id="quiz">
```

A alternativa correta usa:

```html
value="certo"
```

As alternativas incorretas usam:

```html
value="errado"
```

### Mudar Mensagens De Resultado Do Quiz

Abra `script.js` e procure por:

```js
const quizFeedbacks = {
```

Ali ficam as mensagens exibidas conforme a pontuação.

### Mudar A História Em Quadrinhos

Abra `HQ/hq.html`.

Textos da HQ:

- Procure pelos textos dentro de cada `<section class="page">`.
- Cada `section` representa uma página da história.

Imagens da HQ:

- Procure no CSS interno por `#img_chegada`, `#img_trem`, `#img_caminhao` e outros nomes parecidos.
- Troque apenas o caminho dentro de `background-image: url(...)`.

Layout dos quadros:

- Use classes como `panel-full`, `panel-half`, `panel-wide`, `panel-narrow`, `panel-top` e `panel-bottom`.
- As posições dos balões usam classes como `bubble-top-right`, `bubble-bottom-left` e `bubble-bottom-right`.

Acessibilidade da HQ:

- O botão `A+` do site principal também controla a HQ.
- O `script.js` envia tamanho da fonte e alto contraste para o iframe.
- O arquivo `HQ/hq.html` recebe esses dados e aplica o contraste/fonte dentro da própria HQ.

### Adicionar Uma Nova Seção Ao Menu

1. Crie uma nova `<section>` no `index.html` com um `id`.
2. Adicione um novo link no menu apontando para esse `id`.
3. Crie os estilos da nova seção no `style.css`, se precisar.

Exemplo:

```html
<a href="#nova-secao">Nova seção</a>
```

```html
<section id="nova-secao" class="content-section reveal">
```

## Boas Práticas Para Estudantes

- Primeiro altere textos e imagens no `index.html`.
- Depois altere cores e tamanhos no `style.css`.
- Mexa no `script.js` quando a mudança envolver clique, sorteio, quiz, menu ou carrossel.
- Use `Ctrl + F` para procurar por `id`, `class`, textos e nomes de variáveis.
- Teste uma mudança por vez no navegador.
- Se algo sumir, verifique se faltou fechar alguma tag como `</div>`, `</section>` ou `</button>`.

## Mapa Rápido Das Interações

- Botão A+: `script.js`, função `setupAccessibilityMenu`.
- Menu mobile: `script.js`, função `setupMobileMenu`.
- Menu "Explorar": `script.js`, função `setupExploreMenu`.
- Carrossel: `script.js`, funções `setupCarousel`, `changeCarouselSlide`, `transitionToCarouselSlide` e `renderCarouselItem`.
- Curiosidades: `script.js`, função `setupFacts`.
- Quiz: `script.js`, função `setupQuiz`.
- Cards expansivos: `script.js`, função `setupExpandableCards`.
- Animação ao rolar: `script.js`, função `setupScrollReveal`.
