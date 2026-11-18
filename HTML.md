---
title: HTML
---

# 1. Index

<!--toc:start-->

- [1. Index](#1-index)
- [2. HTML](#2-html)
  - [2.1. **_Sintassi_**](#21-sintassi)
- [3. **Markup Semantico**](#3-markup-semantico)
- [4. **Struttura HTML**](#4-struttura-html)
  - [4.1. _Heading_](#41-heading)
  - [4.2. _Paragrafi_](#42-paragrafi)
  - [4.3. _Testo Preformattato_](#43-testo-preformattato)
  - [4.4. _Citazione_](#44-citazione)
  - [4.5. _Divisione_](#45-divisione)
  - [4.6. _Link_](#46-link)
  - [4.7. _Elementi Inline_](#47-elementi-inline)
    - [4.7.1. _Emphasis_, _Strong_, _Small_ e _Barrato_](#471-emphasis-strong-small-e-barrato)
    - [4.7.2. _Corsivo_, _Grassetto_, _Sottolineato_ e _Evidenziato_](#472-corsivo-grassetto-sottolineato-e-evidenziato)
    - [4.7.3. _Codice_](#473-codice)
    - [4.7.4. _Span_, _Vai a capo_](#474-span-vai-a-capo)
  - [4.8. _Immagini_](#48-immagini)
    - [4.8.1. _Image Maps_](#481-image-maps)
  - [4.9. _Liste_](#49-liste)
    - [4.9.1. _Definition List_](#491-definition-list)
  - [4.10. _Carachter Entities_](#410-carachter-entities)
- [5. **Elementi Semantici HTML5**](#5-elementi-semantici-html5)
  - [5.1. _Header_](#51-header)
  - [5.2. _Footer_](#52-footer)
  - [5.3. _Navigation_](#53-navigation)
  - [5.4. _Main_, _Section_ e _Article_](#54-main-section-e-article)
  - [5.5. _Figure_ e _Figurecaption_](#55-figure-e-figurecaption)
  - [5.6. _Aside_](#56-aside)
  - [5.7. _Details_ e _Summary_](#57-details-e-summary)
- [6. **Struttura documento HTML5**](#6-struttura-documento-html5)
  - [6.1. _Metadata_](#61-metadata)
  - [6.2. _Address_](#62-address)
  - [6.3. _Link_](#63-link)
  - [6.4. _Edits_](#64-edits)
  - [6.5. _Contenuti Embedded_](#65-contenuti-embedded)
    - [6.5.1. _Iframe_](#651-iframe)
    - [6.5.2. _Embed_](#652-embed)
    - [6.5.3. _Object_](#653-object)
    - [6.5.4. _Video_](#654-video)
    - [6.5.5. _Audio_](#655-audio)
  - [6.6. **Tabelle**](#66-tabelle)
  - [6.7. **_Form_**](#67-form)
    - [6.7.1. `GET`](#671-get)
    - [6.7.2. _POST_](#672-post)
    - [6.7.3. **Elementi dei form**](#673-elementi-dei-form)
      - [6.7.3.1. `<input>`](#6731-input)
      - [6.7.3.2. `<select>`](#6732-select)
      - [6.7.3.3. _Radio Buttons_ e _Checkboxes_](#6733-radio-buttons-e-checkboxes)
      - [6.7.3.4. `<button>`](#6734-button)
      - [6.7.3.5. _Altri controlli_](#6735-altri-controlli)
- [7. **_Accesibilità al Web_**](#7-accesibilità-al-web)
- [8. Canvas](#8-canvas)
  - [8.1. Curve](#81-curve)
  - [8.2. Inserire immagini](#82-inserire-immagini)
  - [8.3. Inserire Gradienti](#83-inserire-gradienti)
  - [8.4. Pattern di Sfondo](#84-pattern-di-sfondo)
  - [8.5. Scalare oggetti](#85-scalare-oggetti)
  <!--toc:end-->

# 2. HTML

`HTML` è l'acronimo di _HyperText Markup Language_.

I linguaggi di _markup_ sono linguaggi utilizzati per indicare informazioni su testi.

Le annotazioni sono diverse dai testi annotati, che non vengono visualizzati in prima persona.

L'HTML è gestito nella sua evoluzione da `W3C` che si è occupata di definire un linguaggio chiamato `XHTML` che utilizzava una versione più ristretta dello XML (_Extensible Markup Language_), che aveva come obiettivo quello di rendere il rendering delle pagine web più prevedibile.

Ne sono esisiti due versioni:

- _Strict_
- _Transitional_

Nei primi anni 2000 è stato introdotto un **<a src="https://validator.w3.org/">HTML Validator</a>** che verifica che il _markup_ segua le regole dello XHTML .

## 2.1. **_Sintassi_**

I documenti HTML sono composti da contenuto testuale e da elementi HTML.

Gli elementi HTML sono composti da:

- Nome dell'elemento tra parentesi angolari (_tag_)
- Eventuali attributi
- Contenuti del tag

A metà anni 2000 venne proposto una nuova versione `XHTML 2.0`, che cancellava la retrocompabilità con HTML, XHTML 1.0.

Negli stessi anni un working group formato da _Mozilla_ formò il `WHATWG` (_Web HyperText Application Technology Working Group_) che nel 2009 creò lo standard `HTML5`, oggi utilizzato.

```html
<a href="http://www.esempio.com">Esempio</a>
```

Alcuni tag non hanno dei contenuti, ma istruiscono semplicemente il browser a fare qualcosa.

Nelle vecchie versioni di HTML il tag andava chiuso con uno slash, ma questo non è più obbligatorio in _HTML5_.

```html
<img src="file.gif" alt="qualcosa" /> <img src="file.gif" alt="qualcosa" />
```

I _tag_ sono strutture annidabili, infatti spesso un _tag_ (padre) contiene altri _tag_ (figli).

I _tag_ figli devono essere contenuti tra l'apertura e la chiusura dei _tag_ genitori.

```html
<body>
  <p>Questo è un testo <strong>in grassetto</strong></p>
  <h1>Titolo</h1>
</body>
```

# 3. **Markup Semantico**

Negli ultimi anni si è sviluppata la cultura di mantenere nei file HTML solamente la **struttura del documento**.

Tutte le informazioni relative a come le varie parti debbano essere visualizzate si trovano su file `CSS` (_Cascade Style Sheets_).

Con questa divisione si hanno dei vantaggi:

- **Manutenzione**: I file CSS sono più facili da modificare e aggiornare. Permettono di cambiare il look di una pagina in molto meno tempo, in quanto diverse parti di una pagina possono dipendere da una stesso stile CSS;
- **Velocità**: Se indipendenti i file HTML e CSS sono più facili da trasmettere e da scaricare, rispetto che ad unico file con tutto;
- **Accessibilità**: Senza le specifiche di visualizzazione è più facile utilizzare _software di lettura pagina_
- **Ottimizzazioni motori di ricerca**: Senza la parte relativa allo stile, le pagine sono più facili da categorizzare per i motori di ricerca

# 4. **Struttura HTML**

La più facile struttura è la seguente:

```html
<!DOCTYPE html>
<title>Little Hello World!</title>
<p>Hello World!</p>
```

Una pagina più completa è la seguente:

```html
<!DOCTYPE html5>
<html>
  <head lang="it">
    <!-- contiene informazioni sulla pagina, non la pagina -->
    <meta charset="utf-8" />
    <!-- Charset utilizzato -->
    <title>Titolo della pagina</title>
    <!-- Titolo della pagina -->
    <link rel="stylesheets" href="css/main.css" />
    <!-- Risorse esterne riferite da href, rel indica il tipo di file -->
    <script src="js/html5shiv.js"></script>
    <!-- script javascript che viene utilizzato nella pagina -->
  </head>
  <body>
    <!-- corpo del file -->
    <h1>Corpo del file</h1>
    <!-- Heading, testo formattato come titolo -->
    <p>Paragrafo <a href="link.com">1</a></p>
    <!-- Paragrafo con link -->
    <img src="immagine.png" alt="immagine" />
    <!-- Immagini -->
    <div>
      <!-- Contenitore di altri tag, separa più "parti" della pagina -->
      <p>Scritto il <time>25 settembre 2024</time></p>
      <!-- Paragrafo con data-->
    </div>
  </body>
</html>
```

## 4.1. _Heading_

Gli _heading_ `<h#>>` variano da 1 a 6, e formattano i titoli secondo le istruzioni fornite dal browser.
Possono essere facilmente modificati tramite CSS.

> <div class="example" style="display: grid; grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr">
> <div style="border-right: solid 1pt; text-align: center"><h1>H1</h1></div>
> <div style="border-right: solid 1pt; text-align: center"><h2>H2</h2></div>
> <div style="border-right: solid 1pt; text-align: center"><h3>H3</h3></div>
> <div style="border-right: solid 1pt; text-align: center"><h4>H4</h4></div>
> <div style="border-right: solid 1pt; text-align: center"><h5>H5</h5></div>
> <div style="border-right: solid 1pt; text-align: center"><h6>H6</h6></div>
> </div>

## 4.2. _Paragrafi_

Il paragrafo `<p>` è la più basica unità di testo dell'HTML, può contenere HTML e _elementi inline_.

Al termine del paragrafo il browser inserisce un ritorno al carrello (quelli inseriti manualmente non sono presi in considerazione).
Non dovrebbe essere utillizzato quando un elemento più specifico è più adatto.

```html
<p>Sono un paragrafo</p>
```

## 4.3. _Testo Preformattato_

`<pre>` è una sezione di testo dove la struttura è rappresentata dalla convenzione tipografica rispetto dagli elementi.

Alcuni esempi dove è possibile utilizzarlo sono:

- Mail con linee vuote
- Script di codice
- ASCII art

```html
<pre><code> function Panl(element, canClose, closeHandler){
    this.element = element;
    this.canClose = canClose;
    this.closeHandler = function() {if(closeHandler) closeHandler()};
}</code></pre>
```

## 4.4. _Citazione_

Il `<blockquote>` è utilizzato per rappresentare citazioni da altre sorgenti.

E' possibile utilizzare anche il tag `<q>` per citazioni _inline_.

Il tag `<cite>` è quello che rappresenta il titolo della reference, e occasionalmente anche la quote stessa.

```html
<blockquote>
  To be or not to be. -
  <cite><a href="http://www.sorgente.com">Quote famosa</a></cite>
</blockquote>
```

## 4.5. _Divisione_

Il `<div>` è un elemento _container_ che viene utilizzato per effettuare un raggruppamento logico del contesto.

E' spesso utilizzato in combinazione al **CSS** per modificare i suoi contenuti in maniera uniforme.

I suoi attributi più utilizzati sono:

- _class_: identifica la classe CSS da riferire per la formattazione del `<div>`
- _id_
- _lang_: identificare la lingua della porzione di pagina

## 4.6. _Link_

Il link `<a>` ha diversi attributi:

- `href`: Destinazione
- `target`: contesto di browsing per navigazione hyperlink e invio moduli
- `download`: se scaricare la risorsa invece di navigarci
- `rel`: relazione tra il documento nell'hyperlink e la risorsa di destinazione
- `hreflang`: lingua della risorsa linkata
- `type`: informazioni sul tipo della risorsa linkata

I link possono essere a pagine esterne sul web, su parti specifiche della stessa pagina o di altre pagine, o a codice JavaScript.

```html
<a href="http://sito.com">Testo</a>
<a href="http://sito.com/logo.gif"></a>
<a href="index.html">Home</a>
<a href="top">
  <!-- Etichetta sullo stesso sito -->
  <a href="#top">Vai al Top</a>

  <a href="esempio.html#commenti">Commenti</a>
  <a href="mailto:esempio@gmail.com">Mail</a>
  <a href="javascript:OpenPopUp()">Pop Up</a>
  <a href="tel:+39000000">Telefono</a>

  <a href="http://www.unipi.com" target="_blank">new</a>
  <!-- Nuovo Tab -->
  <a href="http://www.unipi.com" target="_self">new</a>
  <!-- Stesso Tab -->
  <a href="http://www.unipi.com" target="_top">new</a>
  <!-- Nuova  --></a
>
```

Ogni risorsa sul WEB ha un suo indirizzo codificato da un codice **URI** (_Uniform Resource Identifier_), che ha il seguente schema: `<scheme>:<scheme-specific-part>`

Lo _scheme_ è il nome del meccanismo utilizzato per accedere alla risorsa (ad esempio il protocollo _http_).
Lo _scheme-specific-path_ è il path specifico (come ad esempio l'indirizzo)

Oltre agli **URI** esistono gli **URN** (_Uniform Resource Name_), che identificano in modo univoco una risorsa, ma non danno informazioni su come accedervi.
L'**URL** (_Uniform Resource Locator_) è un URI che specifica anche come ottenere la rappresentazione della risorsa.

L'**URL** è formato da:

- Protocollo (_http://_), se non è specificato il browser fa la richiesta al server locale
- Nome del dominio
- Path
- Nome del file della risorsa desiderata

La politica che gli indirizzi URL utilizzano è quella del _relative referencing_.
Se tutte le risorse di un file si trovano nella stessa _directory_ è possibile riferirle semplicemente tramite il loro nome.
Tuttavia nella realtà ci sono troppi file per mantenerli in un'unica directory, perciò si utilizzano _pathname relativi_ che precedono il nome del file.
Il _pathname_ dice al browser dove trovare il file sul server, utilizzando convenzioni _Unix_:

- `/`: separano directory tra di loro e dai nomi dei file
- `..`: utilizzati per tornare alla _directory_ al livello superiore rispetto alla nostra posizione attuale.

<img class="75" src="./images/URL Relative Referencing.png">

## 4.7. _Elementi Inline_

Alcuni elementi sono detti _inline_.
Questi elementi non modificano il flusso del testo.

<div class="grid4">
<div class="top">

### 4.7.1. _Emphasis_, _Strong_, _Small_ e _Barrato_

_Emphasis_: `<em>` consiste nel dare enfasi. (simile al corsivo `<i>`)

_Strong_: `<strong>` consiste nel rappresentare elementi importanti (simile al grassetto `<b>`)

_Small_: `<small>` rappresenta commenti secondari.

_Barrato_: `<s>` per informazioni non più accurate.

</div>
<div class="top">

### 4.7.2. _Corsivo_, _Grassetto_, _Sottolineato_ e _Evidenziato_

`<i>` (_italic_) rappresenta il testo in corsivo.

`<b>` (_bold_) rappresenta il testo in grassetto

`<u>` (_underlined_) rappresenta il testo sottolineato

`<mark>` rappresenta del testo evidenziato.

</div>
<div class="top">

### 4.7.3. _Codice_

E' possibile inserire script di codice all'interno della pagina.

I tag sono:

- `<code>` frammento di codice
- `<var>` variabile
- `<samp>` rappresenta l'output da un pezzo di codice
- `<kbd>` rappresenta l'input sul dispositivo
- `<sup>` e `<sub>` rappresentano _superscript_ e _subscript_

</div>
<div class="top">

### 4.7.4. _Span_, _Vai a capo_

L'elemento `<span>` non ha significato da solo ma è utile quando utilizzato in coppia a attributi globali (_class_, _lang_, _dir_)

Il tag `<br>` rappresenta il vai a capo in un testo.

Il tag `<wbr>` invece rappresenta un punto in un paragrafo dove è ammissibile avere un a capo.<br/>
E' utilizzato per avere formati di testi consistenti per tutte le risoluzioni

</div>
</div>

## 4.8. _Immagini_

Sono introdotte dal tag `<img>`, il suo ruolo è quello di rappresentare le immagini, anche se non sono l'unico modo per farlo.

Nel caso in cui le immagini siano il **contenuto** della pagina e non solo per abbellire, allora è il tag corretto da usare.

Gli attributi più importanti sono:

- `src` indica il _path_ dove cercare la risorsa
- `alt` è una breve descrizione dell'immagine per aiutare i servizi di lettura pagina automatica
- `title` è il titolo dell'immagine riportata su un pop-up quando si fa _overlay_
- `width`/`height`: indicano la larghezza/altezza dell'immagine. Possono essere espressi in pixel o in relazione allo spazio dove si trovano (%)

Le immagini si possono trovare in diversi stati:

- _Unavailable_: non sono stati ottenuti dati sull'immagine
- _Partially available_: sono stati ottenuti solo alcuni dati sull'immagini
- _Completely availabe_: sono stati ottenuti tutti i dati dell'immagine
- _Broken_: tutti i dati dell'immagine sono stati ottenti ma non è possibile decodificarla

```html
<img src="images/foto.jpg" alt="Foto" title="Foto" width="80" height="40" />
```

### 4.8.1. _Image Maps_

Le **image maps** sono delle specifiche regioni di un immagine che possono essere associati a link diversi raggiungibili al click dell'utente.

Vengono usati i tag `<map>` con l'attributo _name_ per creare una nuova mappa e i tag `<area>` per definire una nuova area all'interno della mappa.

<img class="60" src="./images/attributi area.png" >

```html
<div>
  <img
    src="planets.gif"
    width="145"
    height="126"
    alt="planets"
    usemap="#planetmap"
  />
  <map name="planetmap">
    <area shape="rect" coords="0,0,82,126" alt="Sun" href="sun.html" />
    <area shape="circle" coords="90,58,3" alt="Mercury" href="mercury.html" />
    <area shape="circle" coords="124,58,8" alt="Venus" href="venus.html" />
  </map>
</div>
```

## 4.9. _Liste_

Sono di due tipi:

- Ordinate (`<ol>`)
- Non ordinate (`<ul>`)

Gli elementi di una listo sono identificati dal tag `<li>`.

Per quanto riguarda le liste ordinate è possibile usare gli attributi;

- `reversed`: ordine inverso
- `start`: indica il numero dal quale partire
- `type`: cosa usare come indice:
  - `1` $\to$ decimali
  - `a` $\to$ lettere minuscole
  - `A` $\to$ lettere maiuscole
  - `i` $\to$ lettere romane minuscole
  - `I` $\to$ lettere romane maiuscole

Per modificare un il valore di un unico elemento della lista si utilizza l'attributo `value`

```html
<ol>
  <li>primo elemento</li>
  <li>
    secondo elemento
    <ol>
      <li>primo elemento del subset del secondo elemento</li>
      <li>secondo elemento del subset del secondo elemento</li>
      <li>terzo elemento del subset del secondo elemento</li>
    </ol>
  </li>
  <li>terzo elemento</li>
</ol>
```

> <ol>
>    <li>primo elemento</li>
>    <li>
>        secondo elemento
>        <ol>
>           <li>primo elemento del subset del secondo elemento</li>
>           <li>secondo elemento del subset del secondo elemento</li>
>           <li>terzo elemento del subset del secondo elemento</li>
>        </ol>
>    </li>
>    <li>terzo elemento</li>
> </ol>

```html
<ul>
  <li>lista 1</li>
  <li>lista 2</li>
  <li>lista 3</li>
</ul>
```

> <ul>
>    <li>lista 1</li>
>    <li>lista 2</li>
>    <li>lista 3</li>
> </ul>

### 4.9.1. _Definition List_

Sono liste di _terms_, dove ognuno ha una sua definizione.

La _definition list_ inizia con il tag `<dl>` <br/>
Ogni _termine_ è rapresentato dal tag `<dt>` <br/>
Ogni _definizione_ inizia con il tag `<dd>`

```html
<dl>
  <dt lang="en-US"><dfn>color</dfn></dt>
  <dt lang="en"><dfn>colour</dfn></dt>
  <dd>
    Sensazione che deriva dalla capacità umana di distinguere gli oggetti dalla
    loro interazione con la luce
  </dd>
</dl>
```

> <dl>
>     <dt lang="en-US"><dfn>color</dfn></dt>
>     <dt lang="en"><dfn>colour</dfn></dt>
>     <dd> Sensazione che deriva dalla capacità umana di distinguere gli oggetti dalla loro interazione con la luce</dd>
> </dl>

## 4.10. _Carachter Entities_

Alcuni caratteri hanno un loro significato e non è possibile inserirli come caratteri di testo.<br/>
Per ovviare a questo problema sono state introdotti le _carachter entities_, alcune sono:

<div class="flexbox" markdown="1">

<table>
    <tr>
        <th>Codice (&...;)</th>
        <th>Rappresentazione</th>
    </tr>
    <tr>
        <td>nbsp</td>
        <td>Nonbreakble space</td>
    </tr>
    <tr>
        <td>lt</td>
        <td><</td>
    </tr>
    <tr>
        <td>gt</td>
        <td>></td>
    </tr>
    <tr>
        <td>copy</td>
        <td>&copy;</td>
    </tr>
    <tr>
        <td>trade</td>
        <td>&trade;</td>
    </tr>
</table>
</div>

# 5. **Elementi Semantici HTML5**

Il problema che nasce all'introduzione di <a href="https://html.spec.whatwg.org/multipage/">HTML5</a> è quello di riempire le pagine web di `<div>`, ognuno che fa riferimento ad un determinato _id_ o _class_ che li fornisce un significato.

Tuttavia in molti casi esiste già un tag specifico che effettua lo stesso lavoro del `<div>`.

Alcuni elementi che troviamo nella maggiorparte dei siti sono:

<div class="grid2">
<div class="top">

## 5.1. _Header_

`<header>` contiene tipicamente:

- Il logo del sito
- Il titolo
- Link di navigazione orizzontale
- Uno o due banner orizzontali

</div>
<div class="top">

## 5.2. _Footer_

`<footer>` contiene solitamente elementi meno importanti:

- Versioni di testo più piccole
- Informaizoni di copyright
- Informazioni sulle policy di privacy del sito
- Link ad altri siti

</div>
</div>

<div class="grid3">
<div class="top">

## 5.3. _Navigation_

`<nav>` rapresenta una sezione dela pagina che contiene link ad altre pagine o ad altre parti della pagina.<br/>
Non ha una sua rappresentaizone particolare.

</div>
<div class="top">

## 5.4. _Main_, _Section_ e _Article_

Il `<main>` ha come scopo quello di contenere il contenuto principale del documento.

La `<section>` rappresenta invece una sezione del documento (titolo, sottotitolo, ...). <br/>
Non è una sezione generica, ma una sezione il cui contenuto ha senso nell'essere esplicitato.

Il tag `<article>` rappresenta una sezione del contenuto che forma una sezione indipendente dal resto del sito

</div>
<div class="top">

## 5.5. _Figure_ e _Figurecaption_

Il tag `<figure>` è utilizzato sia per le immagini che per pezzi di testo essenziali.<br/>
E' utilizzato per raggruppare pezzi della pagina che hanno un'importanza rilevante al documento, ma possono assumere posizioni relative all'interno di esso e non hanno rilevanza sulla propria posizione.

```html
<figure>
  <img src="1.jpg" alt="1" />
  <figcaption>Caption della foto</figcaption>
</figure>
```

</div>
</div>

## 5.6. _Aside_

L'elemento `<aside>` è simile al `<figure>`, e serve a rappresentare una sezione della pagine che consiste in contenuti che sono collegati alla pagina solo tangentalmente, come _sidebars_.

## 5.7. _Details_ e _Summary_

Serve per raggruppare il contenuto di una sezione in un titolo, e espandero qual'ora qualcuno effettui un click.

```html
<details>
  <summary>Immagine</summary>
  ...
</details>
<details>
  <summary>Artista</summary>
  ...
</details>
```

# 6. **Struttura documento HTML5**

La struttura generica di un documento in HTML5 è la seguente:

```html
<!DOCTYPE html>
<html lang="">
  <head>
    <meta charset="utf-8" />
    <title></title>
  </head>
  <body>
    <p>Hello World!</p>
  </body>
</html>
```

## 6.1. _Metadata_

I meta dati sono informazioni su un documento, salvati della sezione `<head>` del documento, perciò non hanno rappresentazione.

```html
<head>
  <meta name="author" content="Mario Rossi" />
  <!-- Informazioni sull'autore della pagina -->

  <meta name="description" content="Un tutorial sull'HTML" />
  <!-- Breve descrizione della pagina -->

  <meta name="generator" content="VSCode" />
  <!-- Informazioni sul software che ha generato la pagina -->

  <meta name="keywords" content="HTML, CSS, XML, JavaScript" />
  <!-- Alcune keyword che riassumono il contenuto della pagina. Utilizzati mai motori di ricerca per selezionare i siti -->

  <base href="http://www.example.com/news/index.html" />
  <!-- Rappresenta l'indirizzo di default utilizzato per accedere agli elementi-->
  <!-- index.html è un place-holder -->

  <title>HTML5 Example</title>
</head>
<body>
  <img src="foto.jpg" alt="foto" />
  <!-- L'indirizzo completo, dato il tag <base> nell'head, è: http://www.example.com/news/foto.jpg -->
</body>
```

Alcuni elementi meta forniscono informazioni a seconda del linguaggio, per facilizzare il filtraggio da parte dei motori di ricerca:

```html
<meta name="keywords" lang="en-us" content="vacation, Greece, sunshine" />
<meta name="keywords" lang="it" content="vacanza, Grecia, alba" />
<meta name="keywords" lang="en" content="holiday, Greecem sunshine" />
```

## 6.2. _Address_

L'elemento `<address>` rappresenta le informazioni di contatto per l'articolo più vicino/elemento body antecedente.

Se l'elemento body del file, allora le informazioni si applicano su tutto il documento.
Non si utilizza per indirizzi arbitrari non connessi con il tema della pagina.
Si trova tipicamente nel `<footer>`.

```html
<address>
  Per maggiori informazioni contattare
  <a href="mailto:jd@esempio.com">Mario Rossi</a>
</address>
```

## 6.3. _Link_

Indica il link ad altri file per ottenervi informazioni (simile ad un `#include`).
A differenza del link `<a>`, questo non è visibile.
Principalmente utilizzato per accedere ai file `CSS` o `JS`.

```html
<head>
  <link rel="stylesheets" type="html/css" href="html5.css" />
  <link rel="stylesheets" type="html/css" href="print.css" media="print" />
  <!-- media indica di usare questo css se si vuole stampare il documento -->
</head>
```

## 6.4. _Edits_

Sono elementi utili per l'editing del testo:

- `<ins>`: rappresenta un aggiunta al documento
- `<del>`: rappresenta una rimossione dal documento
- `<cite>`

L'attributo `datetime` può essere utilizzato per specificare il momento quando c'è stata una rimozione/aggiunta

## 6.5. _Contenuti Embedded_

### 6.5.1. _Iframe_

`<iframe>` rappresente un contesto di browsing innestato. Alcuni attributi:

- `src`: da l'indirizzo del documento che il contesto di browsing innestato ha.
- `srcdoc`: fornisce il contenuto HTML che l'`iframe` contiene (il codice va messo tra le virgolette).
- `sandbox`: fornisce una serie di restrizioni extra per qualsiasi contenuto nell'`iframe`.

```html
<iframe
  sandbox="allow-forms allow-same-origin allow-scripts"
  src="htm26.html"
  width="400"
  height="500"
></iframe>
```

### 6.5.2. _Embed_

`<embed>`: fornisce un punto di integrazione per applicazioni esterne (tipicamente non HTML) o contenuti interattivi.

- `src`: fornisce l'indirizzo della risorsa che sta venedo _embedded_
- `type`: fornisce il `MIME Type` selezionato che deve inizializzare il plugin

```html
<embed src="vowels.swf" width="720" height="500" />
<embed src="movie.mp4" title="Titolo del video" />
```

### 6.5.3. _Object_

`<object>` è la versione moderna di `<embed>`, anche lui fornisce una rappresentazione ad una risorsa esterna.

- `data`: se presente specifica l'indirizzo della risorsa
- `type`: se presente specifica il `tipo MIME` della risorsa
- `typemustwatch`: attributo booleano che indica che la risorsa specificata debba essare usata <u>solo se</u> ha un match di valori con l'attributo `type`

### 6.5.4. _Video_

`<video>` utilizzato per visualizzare video.

- `type`: formato del video
- `autoplay`: se il video inizia con il caricamento della pagina
- `controls`: indica se vedere o meno i controlli video
- `muted`: se togliere l'audio
- `loop`: se quando finisce reinizia
- `poster`: con un URL mostra un'immagine durante il caricamento del video

Può essere accompagnato dal tag dipendente `<source>`.
Questo tag, privo di significato da solo, viene utilizzato per specificare molteplici _risorse media_ per gli elementi.

- `src`: l'indirizzo delle risorse media.

```html
<video src="movie.mp4" type="video/mp4" controls>
  Il video non è disponibile
</video>
<video>
  <source src="movie.mp4" type="video/mp4" />
  <source src="movie.ogg" type="video/ogg" />
</video>
```

### 6.5.5. _Audio_

`<audio>` rappresente un suono o uno stream audio.

I contenuti possono essere forniti da un `src` al'interno del tag, o da molteplici `<source>`

```html
<audio>
  <source src="applausi.ogg" type="audio/ogg" />
  <source src="applausi.mp3" type="audio/mp3" />
  Non supporti gli audio, unlucky
</audio>
```

## 6.6. **Tabelle**

Le tabelle sono create utilizzando il tag `<table>`.

Una tabella HTML contiene un qualsiasi numero di righe `<tr>`.  
Ogni riga contiene delle di colonne `<td>`.

Esiste anche il tag `<th>` (_table heading_) che i browser rappresentano come grassetto.

Alcuni attributi per gli elementi `<td>` e `<th>` sono:

- `colspan="x"`: unisce x colonne
- `rowspan="x"`: unisce x righe

Altri elementi sono:

- `<caption>`: titolo della tabella. Quando rappresentato va sopra la tabella
- `<col>` e `<colgroup>`: possono aiutare nello _styling_
- `<thead>`: può contenere `<tr>` ed è usato per definire il titolo
- `<tfoot>`: può contenere anche `<tr>` ed è usato per inserire delle informazioni a fine tabella. Va inserito **prima** del `<body>` per le versioni prima di HTML5.1
- `<tbody>`: contiene il corpo principale della tabella.

<div class="grid2">
<div class="">

```css
table {
  border: solid 1pt black;
  text-align: center;
  position: relative;
  left: 50%;
  transform: translateX(-50%);
}
caption {
  font-style: italic;
  font-family: "Comic Sans MS", sans-serif;
  font-size: small;
}
tfoot,
thead {
  background-color: lightcoral;
  text-align: center;
}
tfoot tr {
  font-family: "Times New Roman", Times, serif;
  font-size: smaller;
  color: black;
}
thead tr {
  font-weight: bold;
  text-decoration: underline;
  color: white;
}
thead tr th:first-child,
tbody tr td:first-child {
  text-align: left;
  padding-left: 4px;
}
thead tr th:last-child,
tbody tr td:last-child {
  text-align: right;
  padding-right: 4px;
}
tbody tr:nth-child(2n) {
  background-color: lightgray;
  color: black;
}
tbody td {
  border: solid 1pt rebeccapurple;
}
```

</div>
<div class="">

```html
<table>
  <caption>
    La caption della tabella
  </caption>
  <thead>
    <tr>
      <th>Prima Colonna</th>
      <th>Seconda Colonna</th>
      <th>Terza Colonna</th>
    </tr>
  </thead>
  <tfoot>
    <tr>
      <td colspan="3">E' la parte inferiore della tabella</td>
    </tr>
  </tfoot>
  <tbody>
    <tr>
      <td>1:1</td>
      <td>1:2</td>
      <td>1:3</td>
    </tr>
    <tr>
      <td>2:1</td>
      <td>2:2</td>
      <td>2:3</td>
    </tr>
    <tr>
      <td>3:1</td>
      <td>3:2</td>
      <td>3:3</td>
    </tr>
  </tbody>
</table>
```

</div>
</div>

> <div class="flexbox" markdown="1">
> <table style="border: solid 1pt black; text-align: center; position: relative; left: 50%; transform: translateX(-50%);">
>    <caption style="font-style: italic; font-family: 'Comic Sans MS', sans-serif; font-size: small;">La caption della tabella</caption>
>    <thead style="background-color: lightcoral; text-align: center;">
>        <tr style="font-weight: bold; text-decoration: underline; color: white;">
>            <th style="text-align: left; padding-left: 4px;">Prima Colonna</th>
>            <th>Seconda Colonna</th>
>            <th style="text-align: right; padding-right: 4px;">Terza Colonna</th>
>        </tr>
>    </thead>
>    <tfoot style="background-color: lightcoral; text-align: center;">
>        <tr style="font-family: 'Times New Roman', Times, serif; font-size: smaller; color: black;">
>            <td colspan="3">E' la parte inferiore della tabella</td>
>        </tr>
>    </tfoot>
>    <tbody>
>        <tr>
>            <td style="border: solid 1pt rebeccapurple; text-align: left; padding-left: 4px;">1:1</td>
>            <td style="border: solid 1pt rebeccapurple;">1:2</td>
>            <td style="border: solid 1pt rebeccapurple; text-align: right; padding-right: 4px;">1:3</td>
>        </tr>
>        <tr style="background-color: lightgray; color:black;">
>            <td style="border: solid 1pt rebeccapurple; text-align: left; padding-left: 4px;">2:1</td>
>            <td style="border: solid 1pt rebeccapurple;">2:2</td>
>            <td style="border: solid 1pt rebeccapurple; text-align: right; padding-right: 4px;">2:3</td>
>        </tr>
>        <tr>
>            <td style="border: solid 1pt rebeccapurple; text-align: left; padding-left: 4px;">3:1</td>
>            <td style="border: solid 1pt rebeccapurple;">3:2</td>
>            <td style="border: solid 1pt rebeccapurple; text-align: right; padding-right: 4px;">3:3</td>
>        </tr>
>    </tbody>
> </table>
> </div>

## 6.7. **_Form_**

Ci permettono di ricevere informazioni da parte dell'utente, che poi possiamo inviare a server.  
Queste informazioni possono essere:

- Testo
- Password
- Valori predefiniti
- _Checkbox_ o _Radio button_

La struttura del form è la seguente:

<div class="p">

`<form method="get/post" action="file.php">`

</div>

```html
<form method="get" action="process.php">
  <fieldset>
    <legend>Details:</legend>
    <p>
      <label>Title: </label>
      <input type="text" name="title" />
    </p>
    <p>
      <label>Country: </label>
      <select name="where">
        <option>Choose a country</option>
        <option>Canada</option>
        <option>Italy</option>
        <option>United States</option>
      </select>
    </p>
    <input type="submit" disabled />
  </fieldset>
</form>
```

> <form method="get" action="process.php">
>    <fieldset>
>        <legend>Details:</legend>
>        <p>
>            <label>Title: </label>
>            <input type="text" name="title">
>        </p>
>        <p>
>            <label>Country: </label>
>            <select name="where">
>                <option>Choose a country</option>
>                <option>Canada</option>
>                <option>Italy</option>
>                <option>United States</option>
>            </select>
>        </p>
>        <input type="submit" disabled>
>    </fieldset>
> </form>

Quando clicchiamo il pulsante _invia_ avviene un'altra richiesta al server, che consiste generalmente in uno script **PHP** che processerà i dati forniti tramite il form.

Tutti i dati inseriti negli input verranno salvati nell'url della richiesta come:

<div class="p">

`title:valore&where=United+States`

</div>

Questi sono prima codificati (`è` $\to$ `%E9`)

Le caratteristiche essenziali di ogni _form_ sono due:

- **Action**: specifica l'URL _server-side_ che processerà i dati
- **Method**: specifica come la trasmissione dei dati può avvenire:
  - `GET`
  - `POST`

### 6.7.1. `GET`

I dati inviati sono visibili nella barra degli indirizzi e rimangono nella cronologia e nella cache del browser.  
Gli invii possono essere salvati come _bookmark_ e sono soggetti a limite dei caratteri.

<div class="p">

`/process.php?title:titolo&where=Italy http/1.1`

</div>

### 6.7.2. _POST_

I dati inviati sono nascosti dagli utenti e non possono essere salvati da alcuna parte.  
Permette l'invio di dati binari.

<div class="p">

`/process.php http/1.1`
`Date: Sun, 14 Oct 2024 14:49:45 GMT`
`Host: www.mysite.com`
`User-Agent: Movilla/4.0`
`Content-Lenght: 47`
`title:titolo&where=Italy http/1.1`

</div>

### 6.7.3. **Elementi dei form**

<div class="flexbox" markdown="1">

| **Tag**      | **Descrizione**                                                               | **Rappresentazione**                                  |
| ------------ | ----------------------------------------------------------------------------- | ----------------------------------------------------- |
| `<button>`   | Definisce un pulsante cliccabile                                              | <button>Cliccami</button>                             |
| `<datalist>` | (HTML5) Definisce un elenco da utilizzare con altri elementi dei form         |                                                       |
| `<fieldset>` | Raggruppa elementi correlati in un form                                       |                                                       |
| `<form>`     | Definisce il contenitore del form                                             |                                                       |
| `<input>`    | Definisce un campo di input. (HTML5) definisce oltre 20 diversi tipi di input | <input type="text">                                   |
| `<label>`    | Definisce un'etichetta per un elemento di input                               |                                                       |
| `<legend>`   | Definisce l'etichetta per un gruppo di `<fieldset>`                           |                                                       |
| `<option>`   | Definisce un'opzione in un elenco a più elementi                              |                                                       |
| `<optgroup>` | Definisce un gruppo di opzioni correlate in un elenco a più elementi          |                                                       |
| `<select>`   | Definisce un elenco a più elementi                                            | <select><option>1</option><option>2</option></select> |
| `<textarea>` | Definisce una casella di testo a più righe                                    | <textarea></textarea>                                 |

</div>

#### 6.7.3.1. `<input>`

Alcuni valori per l'attributo _type_ del tag `<input>`:

<div class="flexbox" markdown="1">

| Nome                                                          | Descrizione                                                                                                                    | Rappresentazione                                                                                                                                                  |
| ------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `text`                                                        | Crea una casella di testo a riga singola                                                                                       | <input type="text" name="title" />                                                                                                                                |
| `textarea`                                                    | Crea una casella di testo a più righe                                                                                          | <textarea rows="3"> </textarea>                                                                                                                                   |
| `password`                                                    | Crea una casella di testo a riga singola per una password                                                                      | <input type="password" />                                                                                                                                         |
| `file`                                                        | Permette di allegare un file dal computer. È necessario inserire l'attributo `enctype="multipart/form-data"` nel tag `<form>`. | <input type="file"/>                                                                                                                                              |
| `search`                                                      | (HTML5) Crea una casella di testo a riga singola adatta per una stringa di ricerca                                             | <input type="search"/>                                                                                                                                            |
| `email`                                                       | (HTML5) Crea una casella di testo a riga singola adatta per inserire un indirizzo email                                        | <input type="email" />                                                                                                                                            |
| `tel`                                                         | (HTML5) Crea una casella di testo a riga singola adatta per inserire un numero di telefono                                     | <input type="tel"  />                                                                                                                                             |
| `url`                                                         | (HTML5) Crea una casella di testo a riga singola adatta per inserire un URL                                                    | <input type="url" />                                                                                                                                              |
| `number`                                                      | (HTML5) Con gli attributi `min=""` `max=""` permette di validare un numero.                                                    | <input type="number" min="0" max="255" />                                                                                                                         |
| `range`                                                       | (HTML5) Con gli attributi `min=""` `max=""` `step=""` permette di inserire un valore in un range definito.                     | <input type="range" min="0" max="10" step="1" />                                                                                                                  |
| `color`                                                       | (HTML5) Permette di scegliere un colore da una palette.                                                                        | <input type="color" />                                                                                                                                            |
| `date`, `time`, `datetime`, `datetime-local`, `month`, `week` | Sono tutti controlli per la validazione di date e orari.                                                                       | <input type="date" /><br><input type="time" /><br><input type="datetime" /><br><input type="datetime-local" /><br><input type="month" /><br><input type="week" /> |

</div>

E' possibile utilizzare controlli avanzati per alcuni tag:

- `hidden`: Nasconde il tag di input dall'utente. Questo permette di inviare informazioni accessorie senza informare l'utente.
- `Pattern Attribute`: è un modo per validare ciò che l'utente scrive:
- `Datalist`: permette l'autocompletamento a seconda di cosa l'utente scrive

```html
<input
  type="text"
  placeholder="L#L #L#"
  pattern="[a-z][0-9]a-z] [0-9][a-z][0-9]"
/>
<br />
<input type="text" list="cities" name="city" />

<datalist id="cities">
  <option>Calcutta</option>
  <option>Calgary</option>
  <option>London</option>
  <option>Los Angeles</option>
</datalist>
```

> <input type="text" placeholder="L#L #L#" pattern="[a-z][0-9]a-z] [0-9][a-z][0-9]">
> <br>
> <input type="text" list="cities" name="city">
>
> <datalist id="cities">
>    <option>Calcutta</option>
>    <option>Calgary</option>
>    <option>London</option>
>    <option>Los Angeles</option>
> </datalist>

#### 6.7.3.2. `<select>`

L'elemento `<select>` è utilizzato per creare un box multilinea per selezionare uno o più elementi.  
Le opzioni sono definite utilizzando l'elemento `<option>` e possono essere visualizzate su più righe o nascoste.  
Gli elementi possono essere anche raggruppati con l'elemento `<optgroup>`  
Gli elementi `<option>` hanno un attributo <u>opzionale</u> chiamato `value` che invia nel form il suo contenuto invece del testo nel tag.

<div class="grid2">
<div class="">

```html
<select name="choices">
  <option>First</option>
  <option>Second</option>
  <option>Third</option>
</select>
<br />
<br />
<select name="choices2" size="3">
  <option>First</option>
  <option>Second</option>
  <option>Third</option>
</select>
<br />
<br />
<select name="choices3">
  <optgroup label="Nord America">
    <option>Calgary</option>
    <option>Los Angeles</option>
  </optgroup>
  <optgroup label="Europa">
    <option>Londra</option>
    <option>Parigi</option>
    <option>Praga</option>
  </optgroup>
</select>
```

</div>
<div class="">

> <select name="choices">
>     <option>First</option>
>     <option>Second</option>
>     <option>Third</option>
> </select>
> <br>
> <br>
> <select name="choices2" size="3">
>     <option>First</option>
>     <option>Second</option>
>     <option>Third</option>
> </select>
> <br>
> <br>
> <select name="choices3">
>     <optgroup label="Nord America">
>         <option>Calgary</option>
>         <option>Los Angeles</option>
>     </optgroup>
>     <optgroup label="Europa">
>         <option>Londra</option>
>         <option>Parigi</option>
>         <option>Praga</option>
>     </optgroup>
> </select>

</div>
</div>

#### 6.7.3.3. _Radio Buttons_ e _Checkboxes_

Tra i tipi del tag `<input>` ci sono i **Radio Buttons** (`type="radio"`) e le **Checkboxes** (`type="check"`).  
Questi tipi sono utili quando si desidera avere una scelta tra elementi di una piccola lista che si vuole rendere visibile all'utente.

I buttons sono **mutualmente esclusivi**, mentre nelle _checkbox_ più voci possono essere selezionate insieme.

Tra gli attributi opzionale più importanti abbiamo:

- `value`
- `checked`

<div class="grid2">
<div class="">

```html
<input type="radio" name="where" value="1" />America del Nord<br />
<input type="radio" name="where" value="2" checked />Sud America <br />
<input type="radio" name="where" value="3" />Asia<br />

<br /><br />

<label>Accetto i termini</label><input type="checkbox" name="accept" />
<br />
<label>Cosa vorresti visitare?</label><br />
<input type="checkbox" name="visit" checked />Canada<br />
<input type="checkbox" name="visit" />Francia<br />
<input type="checkbox" name="visit" checked />Italia<br />
```

</div>
<div class="">

> <input type="radio" name="where" value="1">America del Nord<br>
> <input type="radio" name="where" value="2" checked>Sud America <br>
> <input type="radio" name="where" value="3">Asia<br>
>
> <label>Accetto i termini</label><input type="checkbox" name="accept">
> <br><br>
> <label>Cosa vorresti visitare?</label><br>
> <input type="checkbox" name="visit" checked>Canada<br>
> <input type="checkbox" name="visit">Francia<br>
> <input type="checkbox" name="visit" checked>Italia<br>

</div>
</div>

#### 6.7.3.4. `<button>`

I _buttons_ sono un altro tipo di input, i più importanti sono:

<div class="flexbox" markdown="1">

| Tipo                    | Descrizione                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `<input type="submit">` | Crea un pulsante che invia i dati del form al server                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `<input type="reset">`  | Crea un pulsante che cancella tutti i dati del form inseriti dall'utente                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `<input type="button">` | Crea un pulsante personalizzato. Questo pulsante potrebbe richiedere _Javascript_ per eseguire effettivamente un'azione                                                                                                                                                                                                                                                                                                                                                                                                 |
| `<input type="image">`  | Crea un pulsante di invio personalizzato che utilizza un'immagine per la sua visualizzazione                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `<button>`              | Crea un pulsante personalizzato. L'elemento `<button>` differisce da `<input type="button">` in quanto puoi personalizzare completamente ciò che appare nel pulsante<br>(includere sia immagini che testo, saltare completamente l'elaborazione lato server usando i collegamenti ipertestuali, ...).<br> Si può trasformare il pulsante in un pulsante di invio usando l'attributo `type="submit"`. <br>Con i pulsanti è più facile applicare gli stili ai contenuti, perché valgono i vari tag `<i>`,`<b>`,`<strong>` |

</div>

#### 6.7.3.5. _Altri controlli_

Ulteriori controlli sono:

- `<progress>` e `<meter>`: forniscono feedback all'utente, ma necessitano di _JavaScript_ per funzionare dinamicamente
- `<output>`: contiene l'output di calcoli

# 7. **_Accesibilità al Web_**

Non tutti gli utenti sono in grado di vedere i contenuti delle pagine web nello stesso modo.  
Il termine si riferisce ale tecnologie di supporto e aòòe feature dell'HTML e del CSS che permettono un utiilizzo semplificato per le persone con disabilità motorie, visive, uditive e cognitive.  
Per migliorare l'accessibilità delle pagine web, è stato creata la <a href="https://www.w3.org/WAI/standards-guidelines/wcag/">**Web Accessibitily Initiative (WAI)**</a>

Alcune linee guida sono:

- Fornire del testo alternativo per ogni contenuto senza testo (immagini, video, ...)
- Creare contenuti che possano essere presentati in formati diversi senza perdere la strutture e le informazioni
- Fare tutte le funzionalità _keyboard-friendly_
- Aiutare l'utente a navigare, trovare elementi e capire la posizione nella pagina

Per le `<table>` si inserisce l'elemento `<caption>`.

Per i `<fieldset>`, `<legend>` e `<lable>` nei `<form>` si inserisce l'attributo `for`, che avrà come contenuto l'`id` del campo di input al quale ci si riferisce.

# 8. Canvas

L'elemento `<canvas>` fornisce script con _resolution-dependent bitmap canvas_ che possono essere utilizzati per effettuare grafici, disegni, immagini al volo.

Due attributi sono utilizzati per gestirne le dimensioni: `wigth` e `height`.

L'_HTML5 Canvas API_ supporta le stesse operazioni di disegno 2D di molti framework moderni.

```html
<canvas> Testo alternativo se non sono supportati </canvas>
```

Possiamo applicare stili CSS all'elemento stesso per aggiungere `border`, `padding` e `margin`.

Alcuni valori del `canvas` vengono ereditate dai suoi elementi (come il `font`).

Alcune proprietà del cancvas seguono la stessa sintassi del CSS.

```html
<!DOCTYPE html>
<html>
  <meta charset="utf-8" />
  <title>Diagonal line example</title>
  <canvas id="example1" style="border: 1px solid;" width="200" height="200">
  </canvas>
</html>
```

```js
function drawLine() {
  const canvas = document.getElementById("example1");
  // Prendiamo il contesto del canvas
  const context = canvas.getContext("2d");

  // Creiamo un nuovo path
  context.beginPath();
  context.moveTo(100, 100); // Spostiamo il punto di partenza
  context.lineTo(130, 180); // Linea dritta fino a ...
  context.lineWidth = 10; // Larghezza linea
  context.strokeStyle = "#00ff00"; // Colore linea
  context.lineCap = "round"; // Stile della fine della linea.
  // Altre sono butt (default), round, square

  // Disegno il percorso sul canvas
  context.stroke();
}
window.addEventListener("load", drawLine, true);
```

Il canvas permette anche di applicare trasformazioni (rotazioni, traslazioni, scala)

Lo stesso codice di prima con una traslazione dell'origine degli assi (impostata di default **in alto a sinistra**):

```js
function drawLine() {
  const canvas = document.getElementById("example2");
  const context = canvas.getContext("2d");

  // Salviamo il contesto attuale
  context.save();

  // Traslo l'origine in (100, 100)
  context.translate(100, 100);

  context.beginPath();
  context.moveTo(0, 0);
  context.lineTo(30, 80);
  context.lineWidth = 10;
  context.strokeStyle = "#00ff00";
  context.lineCap = "round";
  context.stroke();

  // Reimposto il vecchio stato
  context.restore();
}
```

Nel caso di linee chiuse per l'ultimo segmento utilizziamo, invece di `lineTo()`, la funzione `closePath()`.

<div class="grid2">
<div class="">

```js
function drawTopPath(context) {
  context.beginPath();
  context.moveTo(-25, -50);
  context.lineTo(-35, -80);
  context.lineTo(-20, -100);
  context.lineTo(-5, -110);
  context.lineTo(20, -90);
  context.lineTo(40, -80);
  context.lineTo(40, -60);
  context.lineTo(15, -50);

  context.closePath();
}
```

</div>
<div class="">

```js
function drawLandscape() {
  const canvas = document.getElementById("example3");
  const context = canvas.getContext("2d");
  context.save();
  context.translate(100, 200);

  drawTopPath(context);

  context.lineWidth = 4;
  // Angoli tondi
  context.lineJoin = "round";
  // Colore
  context.strokeStyle = "#77BB00";

  // Colore di riempimento
  context.fillStyle = "#339900";
  context.fill();

  // Cambio il colore di riempimento a marrone
  context.fillStyle = "#884400";
  // Il tronco dell'albero
  context.fillRect(-8, -50, 16, 50);

  context.stroke();
  context.restore();
}
window.addEventListener("load", drawLandscape, true);
```

</div>
</div>

## 8.1. Curve

<div class="grid2">
<div class="">

Per disegnare curve si utilizza la funzione

```js
context.quadraticCurveTo(xC, yC, xS, yS);
```

In questo contesto si parte da uno _start point_ e si specificano le coordinate del _Control Point_ (`xC, yC`) e lo _Stop Point_ (`xP, yP`).

</div>
<div class="">
<figure class="100">
<img class="50" src="./images/Canvas/curva di Bezier.png">
<figcaption>

La curva è una curva di Bezier.

</figcaption>
</figure>
</div>
</div>

```js
function createRiver(context) {
  context.beginPath();
  context.moveTo(0, 0);
  context.quadraticCurveTo(150, -180, 460, -140);
  context.strokeStyle = "#5599FF";
  context.lineWidth = 30;
}
```

## 8.2. Inserire immagini

Nei canvas è possibile inserire immagini.
Queste immagini possono essere _stamped_, _stretched_ e modificate tramite trasformazioni.

L'immagine deve essere completamente caricata prima di poterla renderizzare.

```js
// Load the wood image
const wood = new Image();
wood.src = "wood.png";

// Once the image is loaded, draw it on the canvas
wood.onload = function () {
  drawLandscape();
};

function drawLandscape() {
  // ...
  context.drawImage(wood, -8, -50, 16, 50);
}
```

## 8.3. Inserire Gradienti

E' possibile inserire anche dei gradienti per colorare in maniera uniforme una regione.

Per creare un gradiente sono necessari 3 step:

1. Creare l'oggetto
2. Applicare i _color stop_
3. Impostare il gradiente come `fillStyle` o `strokeStyle` a seconda del contesto.

Se alla creazione forniamo due punti $A, B$, il gradiente sarà applicato a tutti gli oggetti che si trovano a cavallo del segmento $AB$

```js
function drawTree(context) {
    // Draw the tree top
    context.lineWidth = 1;

    context.beginPath();
    context.moveTo(-25, -50);
    context.lineTo(-35, -80);
    context.lineTo(-20, -100);
    context.lineTo(-5, -110);
    context.lineTo(20, -90);
    context.lineTo(40, -80);
    context.lineTo(40, -60);
    context.lineTo(15, -50);
    context.closePath();

    // Fill color darker green
    context.fillStyle = '#339900';
    context.fill();
```

```js
// --- Ombra dell'albero --- //
/* Il grandiente diventa più scuro scendendo
 *  dall'alto a sinistra verso in basso a destra
 *  Utilizzando un colore scuro con trasparenza
 */
const topShadow = context.createLinearGradient(-35, -100, 40, -50);

// All'inizo  è nero completamente trasparente
topShadow.addColorStop(0, "rgba(0, 0, 0, 0.0)");
// Alla fine l'ombra non è completamente trasparente
topShadow.addColorStop(0.8, "rgba(0, 0, 0, 0.7)");

context.fillStyle = topShadow;
context.fill();
```

```js
// --- Gradiente orizzontale a 3 step --- //
    const trunkGradient = context.createLinearGradient(-8, -50, 16, -50);
    // Parte sinistra marrone
    trunkGradient.addColorStop(0, '#663300');
    // Parte centrale marrone chiaro
    trunkGradient.addColorStop(0.2, '#996600');
    // Parte destra nera
    trunkGradient.addColorStop(1, '#000000');

    context.fillStyle = trunkGradient;
    context.fillRect(-8, -50, 16, 50);
}

```

## 8.4. Pattern di Sfondo

E' presente un opzione per impostare un'immagine come un pattern che si ripete, sia per i _path_ che per i _fill_:

```js
const water = new Image();
water.src = "water.jpg";
water.onload = function () {
  drawLandscape();
};

function createRiver(context) {
  context.beginPath();

  // The first curve bends up and right
  context.moveTo(0, 0);
  context.quadraticCurveTo(150, -180, 460, -140);

  // Draw the river with a pattern, wide line
  context.strokeStyle = context.createPattern(water, "repeat");
  context.lineWidth = 30;
}
```

I pattern di ripetizione sono:

<div class="flexbox" markdown="1">

| Repeat      | Value                                                    |
| ----------- | -------------------------------------------------------- |
| `repeat`    | (_default_) L'immagine è ripetuta in tutte le dimensioni |
| `repeat-x`  | L'immagine è ripetuta solo nella direzione X             |
| `repeat-y`  | L'immagine è ripetuta solo nella direzione Y             |
| `no-repeat` | L'immagine è mostrata una volta e non è ripetuta         |

</div>

## 8.5. Scalare oggetti

Le trasformazioni come la `scale` e la `rotate` operano in **riferimento all'origine**.

Se si effettua una rotazione di una figura che non è centrata enll'origine, la figura ruoterà sia su se stessaa che rispetto all'origine.
Questo accade anche per la `scale`, che moltiplicherà per il fattore di scala anche le coordinate.

```js
classontext.save();
context.translate(100, 250);
drawTree(context);
context.stroke();
context.restore();
context.save();
context.translate(200, 180);
context.scale(1.2, 1.2);
drawTree(context);
context.stroke();
context.restore();
context.save();
context.translate(50, 170);
context.scale(0.8, 1.4);
drawTree(context);
context.stroke();
context.restore();
```
