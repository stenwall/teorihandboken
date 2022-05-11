---
layout: default
title: HTML
parent: HTML & CSS (HC)
nav_order: 1
---

# HC 1.1-1 HTML
{: .fs-9 .fw-700 .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

HTML står för HyperText Markup Language. Markup Language = “märkspråk”, för att märka upp delar av text. Texten tolkas av webbläsaren, och översätter det till det vi ser på skärmen. HTML skrivs som dokument, och är uppbyggt av element med taggar (`<>`) och innehåll. Dokumentets filnamn slutar med `.html`.

W3C har standardiserat markup-språket, och nuvarande iteration är ganska fritt och inte så strikt, där de flesta browsers fyller i eventuella fel. Nuvarande standard är HTML 5.2 (HTML5).

---

## Struktur

Det finns en tydlig uppbyggnad/struktur för hur HTML-dokument skrivs:

```html
<!DOCTYPE html> // anger att vi använder HTML 5
<html> // rotelement, innehåller hela dokumentträdet
  <head> // innehåller metadata, inget av detta är synligt på sidan
    <title>Sidans titel</title>
    // titeln som visas högst upp i browserfönstret
  </head> // slut tagg för head
  <body> // allt innehåll som ska synas på sidan skrivs inom body taggen
  </body> // slut tagg för body
</html> // slut tagg för rotelementet
```

---

## Element

Ett HTML-element är det som ryms inom taggarna `<>`. Det är uppbyggt efter följande struktur:
![html-syntax](../assets/html-tag.png)

Element kan ha en uppsjö av olika attribut, där de vanligaste är `class` och `id`, som används både vid styling och för att manipulera DOM:en med till exempel JavaScript. Flera element kan ha samma `class`, medan `id` alltid måste vara unikt.

### Semantik

Det finns olika typer av element beroende på innehåll, till exempel används `<img>`-taggen för bilder och `<a>`-taggen för länkar. För text finns det en uppsjö av olika taggar, där den vanligaste kanske är `<div>`, men vi har ingen aning om vad det elementet innehåller baserat på namnet. Där kommer semantiska element in. I ett semantiskt element ser vi rollen elementet har i namnet.

#### Exempel
{:.no_toc}

- `<section>` - sektion runt specifikt tema
- `<article>` - fristående text som t.ex. blogginlägg
- `<nav>` - navigationen/menyn
- `<aside>` - utfyllande innhehåll som t.ex. sidebars
- `<header>` - sidans header, som är högst upp
- `<footer>` - sidans footer, längst ner
- `<p>` - en sammanhängande paragraf
- `<address>` - alla typer av kontaktuppgifter

Att använda semantiska element istället för generiska som `<div>` och `<span>` ökar tillgängligheten, då skärmläsare vet vilken typ av text eller information som elementet innnehåller. Det ger också bättre ranking i sökmotorer.

### Blocknivå vs. inlinenivå

Ett element på blocknivå börjar alltid på en ny rad, och har inga andra element bredvid sig. De får automatiskt margins uppe och nere, om inte annat anges i stylingen. [^1]

#### Exempel på blockelement
{:.no_toc}

- `<h1>` - headline/rubrik element (i storlek 1-6)
- `<ul>` - unordered list; punktlista
- `<ol>` - ordered list; numrerad lista
- `<li>` - listelement (punkterna i listorna ovan)
- `<p>` - paragraf
- `<table>` - tabelldata, mer om det nedan
- `<div>` - generiskt blockelement

Ett element på inline tar till skillnad från blockelement bara upp så mycket bredd de behöver. De kan ha andra inline element bredvid sig, och de kan vara mitt i en text i en paragraf till exempel. Inlineelement har inga marginaler om det inte anges i stylingen.

#### Exempel på inlineelement
{:.no_toc}

- `<a>` - länkar
- `<b>` - fetstilt text
- `<sub>` - subscript (nedsänkt)
- `<sup>` - superscript (upphöjt)
- `<span>` - generiskt inlinelement

---

## Övrig syntax

### Kommentarer

För att kommentera ut text i ett HTML-dokument används `<!-- -->`.

#### Exempel
{:.no_toc}

```html
<body>
  <div class="container">
    <h1>Rubrik</h1>
    <!-- Den här kommentaren syns inte på sidan -->
    <p>En paragraf med text om något.</p>
  </div>
</body>
```

### Entiteter

Entiteter används för att visa "reserverade" tecken som annars kan tolkas som HTML av webbläsaren, eller för att skriva ut symboler som inte går att skriva ut med vanligt tangentbord utan måste copy-pastas (som till exempel emojis). HTML-entiteter börjar med ampersand och slutar med semicolon. [^2]

#### Exempel
{:.no_toc}

- `&gt;` - större än (`>`)
- `&lt;` - mindre än (`<`)
- `&amp;` - ampersand (`&`)
- `&nbsp;` - mellanslag/space som ej ska radbrytas
- `&copy;` - copyright symbol (`©`)

---

## Tabeller

För att visa data i tabeller används en viss syntax och struktur, som är viktig både för styling och semantik.

#### Exempel
{:.no_toc}

```html
<table> //rotelement för tabellen
  <thead> //table head
    <tr> //table row
      <th></th> //table heading
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody> //table body
    <tr>
      <td></td> //table data
      <td></td>
      <td></td>
    </tr>
  </tbody>
</table>
```

### Scope

I tabellelement kan också `scope` användas för att öka tillgängligheten.

#### Syntax
{:.no_toc}

```html
<th scope="col|row|colgroup|rowgroup"></th>
```

#### Förklaring
{:.no_toc}

- `col` - cellen är heading till en column
- `row` - cellen är heading till en rad
- `colgroup` - cellen är heading till en grupp kolumner
- `rowgroup` - cellen är rubrik till en grupp rader

---

### Attribut

Cellerna kan också vara olika stora, det vill säga sträcka sig över flera rader eller flera kolumner. Då används attributen `rowspan="<siffra>"` och `colspan="<siffra>"`.

#### Exempel [^3]
{:.no_toc}

```html
<table>
  <tr>
    <th colspan="3">2022</th>
  </tr>
  <tr>
    <th rowspan="2" colspan="2">APRIL</th>
    <td></td>
  </tr>
  <tr>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>
```

<table>
  <tr>
    <th colspan="3">2022</th>
  </tr>
  <tr>
    <th rowspan="2" colspan="2">APRIL</th>
    <td></td>
  </tr>
  <tr>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>

---

## Formulär

Likt för tabeller används också särskilda element och attribut för formulär. Rootelementet för ett formulär är `<form>`, `<input>` för input field (inmatningsfält) och `<label>` används som etikett/beskrivning till ett input field. För att koppla ihop ett label-element med ett input-element används input-elementets id.

I rootelementet (`<form>`) anges vilken action som ska tas när formuläret submittas/skickas, och med vilken metod.

#### Exempel
{:.no_toc}

```html
<form action="/my-handling-form-page" method="post">
  <fieldset>
    <legend>Fyll i dina uppgifter</legend>
    <label for="name">Användarnamn</label>
    <input type="text" id="name" name="user_name" />
    <label for="mail">E-mail</label>
    <input type="email" id="mail" name="user_email" />
    <label for="msg">Meddelande</label>
    <textarea id="msg" name="user_message"></textarea>
    <button type="submit">Skicka</button>
  </fieldset>
</form>
```

<style>
  #li1:before,
  #li2:before,
  #li3:before,
  #li4:before {
    content: '';
  }
</style>
<form action="/my-handling-form-page" method="post">
  <fieldset>
    <legend>Fyll i dina uppgifter</legend>
    <ul style="list-style: none; padding: 0; margin: 0;">
      <li id="li1">
        <label
          for="name"
          style="display: inline-block; width: 120px; text-align: right;"
          >Användarnamn</label
        >
        <input
          type="text"
          id="name"
          name="user_name"
          style="width: 300px; box-sizing: border-box;"
        />
      </li>
      <li id="li2">
        <label
          for="mail"
          style="display: inline-block; width: 120px; text-align: right;"
          >E-mail</label
        >
        <input
          type="email"
          id="mail"
          name="user_email"
          style="width: 300px; box-sizing: border-box;"
        />
      </li>
      <li id="li3">
        <label
          for="msg"
          style="display: inline-block; width: 120px; text-align: right;"
          >Meddelande</label
        >
        <textarea
          id="msg"
          name="user_message"
          style="width: 300px; box-sizing: border-box; vertical-align: top;"
        ></textarea>
      </li>
      <li id="li4" style="padding-left: 120px;">
        <button type="submit" style="margin-left: .25em;">Skicka</button>
      </li>
    </ul>
  </fieldset>
</form>

Input fields kan vara av olika sorter, som till exempel checkbox som är en ruta som kan klickas i och radio button där bara en ruta i en grupp kan väljas. Se exempel nedan.

### Olika typer av input fields [^4]

#### Text

```html
<label for="username">Användarnamn</label>
<input type="text" id="username" name="username" value="Fyll i användarnamn" />
```

<label for="username">Användarnamn</label>
<input type="text" id="username" name="username" value="Fyll i användarnamn">

#### Password

```html
<label for="pwd">Lösenord</label>
<input type="password" id="pwd" name="pwd" value="lösenord" />
```

<label for="pwd">Lösenord</label>
<input type="password" id="pwd" name="pwd" value="lösenord">

#### Radio button

```html
<fieldset>
  <legend>Välj måltid</legend>
   <label for="soup">Soppa</label>
   <input type="radio" id="soup" name="meal" value="soup" checked />
   <label for="salad">Sallad</label>
   <input type="radio" id="salad" name="meal" value="salad" />
   <label for="pizza">Pizza</label>
   <input type="radio" id="pizza" name="meal" value="pizza" />
</fieldset>
```

<style>
  #li9:before,
  #li10:before,
  #li11:before {
    content: '';
  }
</style>
<fieldset>
  <legend>Välj måltid</legend>
  <ul>
    <li id="li9">
      <label for="soup">Soppa</label>
      <input type="radio" id="soup" name="meal" value="soup" checked />
    </li>
    <li id="li10">
      <label for="salad">Sallad</label>
      <input type="radio" id="salad" name="meal" value="salad" />
    </li>
    <li id="li11">
      <label for="pizza">Pizza</label>
      <input type="radio" id="pizza" name="meal" value="pizza" />
    </li>
  </ul>
</fieldset>

#### Checkbox

```html
<fieldset>
  <legend>Välj topping</legend>
   <label for="cheese">Ost</label>
   <input type="checkbox" id="cheese" name="topping" value="cheese" checked />
   <label for="tomato">Tomat</label>
   <input type="checkbox" id="tomato" name="topping" value="tomato" />
   <label for="mushroom">Svamp</label>
   <input type="checkbox" id="mushroom" name="topping" value="mushroom" />
   <label for="garlic">Vitlök</label>
   <input type="checkbox" id="garlic" name="topping" value="garlic" />
</fieldset>
```

<style>
  #li5:before,
  #li6:before,
  #li7:before,
  #li8:before {
    content: '';
  }
</style>
<fieldset>
  <legend>Välj topping</legend>
  <ul>
    <li id="li5">
      <label for="cheese">Ost</label>
      <input
        type="checkbox"
        id="cheese"
        name="topping"
        value="cheese"
        checked
      />
    </li>
    <li id="li6">
      <label for="tomato">Tomat</label>
      <input type="checkbox" id="tomato" name="topping" value="tomato" />
    </li>
    <li id="li7">
      <label for="mushroom">Svamp</label>
      <input type="checkbox" id="mushroom" name="topping" value="mushroom" />
    </li>
    <li id="li8">
      <label for="garlic">Vitlök</label>
      <input type="checkbox" id="garlic" name="topping" value="garlic" />
    </li>
  </ul>
</fieldset>

---

## Referenser

[^1]: [Difference between block elements and inline elements - GeeksforGeeks](https://www.geeksforgeeks.org/difference-between-block-elements-and-inline-elements/)
[^2]: [MDN Glossary - Entity](https://developer.mozilla.org/en-US/docs/Glossary/Entity)
[^3]: [W3 Schools: HTML Tutorial - Table Colspan & Rowspan](https://www.w3schools.com/html/html_table_colspan_rowspan.asp)
[^4]: [MDN Guides - Basic native form controls](https://developer.mozilla.org/en-US/docs/Learn/Forms/Basic_native_form_controls)
