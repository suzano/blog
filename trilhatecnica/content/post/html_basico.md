---
title: HTML - Elementos Básicos
description: Artigo de exemplo que contém elementos HTML básicos para formatação de texto na Web.
date: 2023-01-10
thumbnail:
  src: "assets/images/html_basico/html.jpg"
categories:
  - "Desenvolvimento"
tags:
  - "HTML"
  - "CSS"
  - "Markdown"
draft: true
---

O principal objetivo deste artigo é garantir que todos os elementos HTML básicos sejam decorados com CSS para não perder nenhum elemento possível.

<!--more-->

## Títulos

Vamos começar com todos os títulos possíveis. Os elementos HTML `<h1>`—`<h6>` representam seis níveis de cabeçalhos de seção. `<h1>` é o nível de seção mais alto e `<h6>` é o mais baixo.

# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6

***

## Parágrafo

De acordo com a [especificação HTML5](https://www.w3.org/TR/html5/dom.html#elements) pela [W3C](https://www.w3.org/), **documentos HTML consistem de uma árvore de elementos e texto**. Cada elemento é indicado na fonte por uma [tag de início](https://www.w3.org/TR/html5/syntax.html#syntax-start-tags), como `<body>`, e uma [tag final](https://www.w3.org/TR/html5/syntax.html#syntax-end-tags), como `</body>`. (*Certas tags iniciais e finais podem, em certos casos, ser omitidas e estão implícitas em outras tags.*)

Os elementos podem ter atributos, que controlam como os elementos funcionam. Por exemplo, hiperlinks são formados usando o elemento `a` e seu atributo `href`.

## Tipos de Lista

### Lista Ordenada

1. Primeiro item
2. Segundo item
3. Terceiro item

### Lista Não Ordenada

* Item da lista
* Outro artigo
* E outro item

### Lista Aninhada

<ul>
  <li>Primeiro item</li>
  <li>Segundo item
    <ul>
      <li>Segundo item Primeiro subitem</li>
      <li>Segundo item Segundo subitem</li>
        <ul>
          <li>Segundo item Segundo subitem Primeiro sub-subitem</li>
          <li>Segundo item Segundo subitem Segundo sub-subitem</li>
          <li>Segundo item Segundo subitem Terceiro sub-subitem</li>
        </ul>
      </li>
      <li>Segundo item Terceiro subitem
        <ol>
          <li>Second item Third subitem First sub-subitem</li>
          <li>Second item Third subitem Second sub-subitem</li>
          <li>Second item Third subitem Third sub-subitem</li>
        </ol>
    </ul>
  </li>
  <li>Third item</li>
</ul>

### Lista de Definições

HTML também suporta listas de definição.

<dl>
  <dt>Blanco tequila</dt>
  <dd>The purest form of the blue agave spirit...</dd>
  <dt>Reposado tequila</dt>
  <dd>Typically aged in wooden barrels for between two and eleven months...</dd>
</dl>

## Blockquotes

The blockquote element represents content that is quoted from another source, optionally with a citation which must be within a `footer` or `cite` element, and optionally with in-line changes such as annotations and abbreviations.

> Quoted text.
> This line is part of the same quote.
> Also you can *put* **Markdown** into a blockquote.

Blockquote with a citation.

<blockquote>
  <p>My goal wasn't to make a ton of money. It was to build good computers. I only started the company when I realized I could be an engineer forever.</p>
  <footer>— <cite>Steve Wozniak</cite></footer>
</blockquote>

According to Mozilla's website, <q cite="https://www.mozilla.org/en-US/about/history/details/">Firefox 1.0 was released in 2004 and became a big success.</q>

## Tables

Tables aren't part of the core Markdown spec, but Hugo supports them.

| ID  | Make      | Model   | Year |
| --- | --------- | ------- | ---- |
| 1   | Honda     | Accord  | 2009 |
| 2   | Toyota    | Camry   | 2012 |
| 3   | Hyundai   | Elantra | 2010 |

Colons can be used to align columns.

| Tables      | Are           | Cool         |
|:----------- |:-------------:| ------------:|
| align: left | align: center | align: right |
| align: left | align: center | align: right |
| align: left | align: center | align: right |

You can also use inline Markdown.

| Inline     | Markdown  | In                | Table      |
| ---------- | --------- | ----------------- | ---------- |
| *italics*  | **bold**  | ~~strikethrough~~ | `code`     |

## Code

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Example HTML5 Document</title>
</head>
<body>
  <p>Teste</p>
</body>
</html>
```

{{< highlight html >}}
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Example HTML5 Document</title>
</head>
<body>
  <p>Test</p>
</body>
</html>
{{< /highlight >}}

## Other stuff — abbr, sub, sup, kbd, etc.

<abbr title="Graphics Interchange Format">GIF</abbr> is a bitmap image format.

H<sub>2</sub>O

C<sub>6</sub>H<sub>12</sub>O<sub>6</sub>

X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>

Press <kbd>X</kbd> to win. Or press <kbd><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>F</kbd></kbd> to show FPS counter.

<mark>As a unit of information in information theory, the bit has alternatively been called a shannon</mark>, named after Claude Shannon, the founder of field of information theory.
