---
title: CSS
---

# 1. Index

<!--toc:start-->

- [1. Index](#1-index)
- [2. CSS](#2-css)
  - [2.1. **Sintassi**](#21-sintassi)
  - [2.2. _Locazioni dei file_](#22-locazioni-dei-file)
    - [2.2.1. _Selettori_](#221-selettori)
    - [2.2.2. _Selettori ID_](#222-selettori-id)
    - [2.2.3. _Selettori di Attributi_](#223-selettori-di-attributi)
    - [2.2.4. Selettori di Contesto](#224-selettori-di-contesto)
  - [2.3. **Interazione tra gli stili**](#23-interazione-tra-gli-stili)
    - [2.3.1. _Ereditarietà_](#231-ereditarietà)
    - [2.3.2. _Specificità_](#232-specificità)
    - [2.3.3. _Posizione_](#233-posizione)
  - [2.4. **Modello Box**](#24-modello-box)
    - [2.4.1. _Background_](#241-background)
    - [2.4.2. _Border_, _Margin_ e _Padding_](#242-border-margin-e-padding)
    - [2.4.3. `width` e `height`](#243-width-e-height)
  - [2.5. **Stili di Testo**](#25-stili-di-testo)
- [3. **CSS Avanzato: _Layout_**](#3-css-avanzato-layout)
  - [3.1. **Grid Layout**](#31-grid-layout)
  - [3.2. **Posizione degli elementi**](#32-posizione-degli-elementi)
  - [3.3. **Elementi fluttuanti** (`float`)](#33-elementi-fluttuanti-float)
  - [3.4. **Layout Multicolonna**](#34-layout-multicolonna)
    - [3.4.1. _Float Approach_](#341-float-approach)
    - [3.4.2. _Positioning Approach_](#342-positioning-approach)
    - [3.4.3. _Flexbox Approach_](#343-flexbox-approach)
  - [3.5. **Layout CSS**](#35-layout-css)
    - [3.5.1. _Fixed Layout_](#351-fixed-layout)
    - [3.5.2. _Liquid Layout_](#352-liquid-layout)
    - [3.5.3. _Hybrid Layout_](#353-hybrid-layout)
  - [3.6. **Responsive Design**](#36-responsive-design)
    - [3.6.1. _Media Queries_](#361-media-queries)
      - [3.6.1.1. _Menù_](#3611-menù)
  - [3.7. **Filtri, Transizioni e Animazioni**](#37-filtri-transizioni-e-animazioni)
  <!--toc:end-->

# 2. CSS

Tramite il CSS possiamo modificare:

- Proprietà dei font
- Colori
- Dimensioni
- Bordi
- Immagini di sfondo
- Proporzioni degli elementi

Come tutti i linguaggi ha una sua sintassi, e può essere aggiunto:

- Direttamente nell'elemento `<head>`
- In un file separato .css riferito tramite `<link>`

Il CSS è stato introdotto per diversi motivi:

- Le potenzialità del CSS sono molte di più rispetto alla formattazione disponibile da HTML
- E' possibile gestire meglio le pagine, in quanto gli stili possono essere salvati in uno o più file assestanti per poterli riutilizzare e rendere le pagine più leggere
- I siti sviluppati con CSS sono più accessibili
- Diminuisce la velogità di ricezione delle pagine HTML, in quanto più leggere
- E' possibile fornire diverse rappresentazioni di una stessa pagina a seconda di browser/dispositivi/...

Tuttavia non è stato sviluppato per essere un _layout language_, perciò è possibile che si possano riscontrare problematiche quando si gestiscono _floating elements_, posizioni _relative_, altezze incosistenti, margini sovrapposti, nomi di proprietà poco intuitivi.

Esistono più versioni di CSS:

- 1996: W3C pubblica il **<u>CSS Level 1</u>**
- 1997: W3C pubblica il **<u>CSS2</u>** (_Level 2 Reccomendation_)
- 2011: W3C rende ufficiale **<u>CSS2.1</u>**

Dall'ultima modifica si sta lavorando sul **<u>CSS3</u>** _draft_. <br>
Di questa versione ad oggi sono ufficiali:

- CSS Selectors
- CSS Namespace
- CSS Media Queries
- CSS Color
- CSS Style Attributes

## 2.1. **Sintassi**

In CSS i commenti si scrivono così: `/*...*/`.
Un file CSS è composto da una o più **regole di stile**.

Una regola consiste da:

- _Selector_: identifica l'elemento HTML che verrà influenzato
- _Declaretion Block_: Contiene una serie di Proprietà e Valori. Le proprietà sono divise dal carattere `;`, mentre per assegnare un valore ad una proprietà si usa il carattere `:`

```css
selector {
  property1: value;
  /*...*/
  propertyn: value;
}

em {
  color: red;
}

p {
  margin: 5px 0 10px 0;
  font-weight: bold;
  font-family: Arial, Helvetica, sans-serif;
}
```

I valori possono essere di due tipi:

- _keyword_: alcune proprietà hanno delle _keyword_ proprie (`text-align: center`)
- Valori con/senza unità di misura

Un esempio è con i colori, che nelle vecchie versioni non avevano molte rappresentazione con _keyword_, mentre nelle ultime versioni sono molte di più.

```css
p {
  color: blue;
}

span {
  color: #0000ff;
}

td {
  color: rgb(0, 0, 255, 1);
  /* L'ultimo valore è la trasparenza [0, 1] */
}

tr {
  color: hsl(255, 100%, 50%);
}
```

Le unità di misura sono di due tipi:

- **Relative**: dimensioni basate sui valori di qualcos'altro, come l'elemento genitore
- **Assolute**: non dipendono dal contensto della pagina

Alcune unità di misura sono le seguenti:

<div class="flexbox" markdown="1">

|   Unità    | Descrizione                                                                                                                                                                                                                              |      Tipo       |
| :--------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------: |
|    `em`    | Uguale al valore calcolato della proprietà `font-size` dell'elemento su cui viene utilizzato.<br>Quando utilizzato per le dimensioni del carattere, l'unità `em` è in relazione alla dimensione del carattere del padre.                 |    Relativo     |
|    `%`     | Una misura che è sempre relativa ad un altro valore.<br>Il significato preciso di % varia a seconda della proprietà a cui si riferisce.                                                                                                  |    Relativo     |
|    `ex`    | Una misura relativa raramente usata che esprime la dimensione in relazione all'altezza x del font di un elemento.                                                                                                                        |    Relativo     |
|    `ch`    | Un'altra misura relativa raramente usata.<br> Questa esprime la dimensione in relazione alla larghezza del carattere zero `0` del font di un elemento.                                                                                   | Relativo (CSS3) |
|   `rem`    | Sta per _root-em_, che è la dimensione del font dell'elemento radice.<br> A differenza di `em`, che può essere diverso per ogni elemento, il `rem` è costante in tutto il documento.                                                     | Relativo (CSS3) |
| `vw`, `vh` | Stanno per larghezza e altezza del _viewport_ (finestra del browser).<br> Entrambi sono valori percentuali (tra 0 e 100) del _viewport_.<br>Ciò consente a un elemento di cambiare dimensione quando il _viewport_ viene ridimensionato. | Relativo (CSS3) |

</div>

## 2.2. _Locazioni dei file_

Esistono 3 tipi di fogli di stile:

- **Author Created style sheets**: creati dall'autore della pagina
- **User style Sheets**: definiti dal un signolo utente, possono sovrascrivere altre regole
- **Browser Style Sheets**: definiti dal browser

Le regole di stile possono trovarsi in 3 diverse locazioni (utilizzabili in combinazione):

- **Inline** (brutta usanza, da fare il meno possibile)
- **Embedded** (meglio degli inline, usalo il meno possibile)
- **External**

```html
<head>
  <meta charset="utf-8" />
  <!-- Embedded -->
  <style>
    h1,
    h2,
    h3 {
      text-align: center;
    }
    h3 {
      font-size: 18pt;
      font-weight: bold;
    }
  </style>

  <!-- External -->
  <link rel="stylesheet" href="styles.css" />
</head>

<!-- Inline -->
<h2 style="font-size: 24pt;">Share your Travels</h2>
<h2 style="font-size: 24pt; font-weight: bold;">Description</h2>
<h3>New York - Central Park</h3>
```

> <h2 style="font-size: 24pt;">Share your Travels</h2>
> <h2 style="font-size: 24pt; font-weight: bold;">Description</h2>
> <h3>New York - Central Park</h3>

### 2.2.1. _Selettori_

I selettori utilizzano nomi degli elementi HTML.
Possono essere selezionati <u>tutti</u> gli elementi tramite il _selettore di elementi universale_ `*`.

E' possibile raggruppare diversi selettori tramite virgole.
Ciò diminuisce sensibilmente la dimensione e la complessità del file CSS, combinando più regole in una sola.
L'utilizzo principale è quello di resettare in maniera rapida degli elementi da eventuali stili del browser.

```css
p,
div,
aside {
  margin: 0;
  padding: 0;
}

html,
body,
div,
span,
h1,
h2,
h3,
h4,
h5,
h6,
p {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  vertical-align: baseline;
}
```

Oltre ai tag HTML, è possibile utilizzare **selettori di classe** (preceduti da un punto).

Questi selettori ci permettono di modificare diversi elementi senza considerare la loro posizione, semplicemente assegnando ad un determinato tag **lo stesso valore all'attributo class**.

```html
<head>
  <style>
    .first {
      font-style: italic;
      color: red;
    }
  </style>
</head>
<body>
  <h2 class="first">Recensioni</h2>
  <div>
    <p class="first">Da riccardo</p>
    <p>Fa cagare</p>
  </div>
  <hr />
  <div>
    <p class="first">Da Susan</p>
    <p>Figo</p>
  </div>
</body>
```

> <h2 style="font-style: italic; color: red;">Recensioni</h2>
> <div>
>     <p style="font-style: italic; color: red;"> Da riccardo</p>
>     <p> Fa cagare </p>
> </div>
> <div>
>     <p class ="first">Da Susan</p>
>     <p>Figo </p>
> </div>

### 2.2.2. _Selettori ID_

Permetto di accedere un elemento specifico tramite il suo attributo id. <br>
Il nome nel file CSS è preceduoto da un `#`.

Gli ID sono utilizzati **<u>UNA VOLTA</u>** per pagina, in un unico elemento.

```html
<head>
  <style>
    #latestComment {
      font-style: italic;
      color: red;
    }
  </style>
</head>
<body>
  <h2 class="first">Reviews</h2>
  <div id="latestComment">
    <p class="first">By Ricardo on <time>2016-05-23</time></p>
    <p>Easy on the HDR buddy.</p>
  </div>
  <hr />
  <div>
    <p class="first">By Susan on <time>2016-11-18</time></p>
    <p>I love Central Park.</p>
  </div>
  <hr />
</body>
```

> <style>
> #latestComment{
>     font-style: italic;
>     color: red;
> }
> </style>
>
> <h2 class="first">Reviews</h2>
> <div class=".div" id="latestComment">
>     <p class="first">By Ricardo on <time>2016-05-23</time></p>
>     <p>Easy on the HDR buddy.</p>
> </div>
> <hr/>
> <div class=".div">
>     <p class="first">By Susan on <time>2016-11-18</time></p>
>     <p>I love Central Park.</p>
> </div>
> <hr/>

### 2.2.3. _Selettori di Attributi_

E' un modo di selezionare elementi HTML a seconda della presenza o del valore di un attributo. <br>
Sono circondati da parentesi quadre:

- `[a]`: presenza
- `[a=b]` presenza e valore di $b$
- `[a~=b,c]`: presenza e valori possibili
- `[a^=b]`: presenza e valori che _iniziano_ per $b$
- `[a*=b]`: presenza e deve essere contenuto $b$ nel valore
- `[a$=b]`: presenza e valori che _terminano_ per $b$

```html
<head lang="en">
  <style>
    [align] {
      color: green;
    }
  </style>
</head>
<body>
  <div>
    <p align="center">Canada is a North American country consisting of ...</p>
    <p>Eh già</p>
  </div>
</body>
```

> <p style="text-align:center; color:green" align="center">Canada is a North American country consisting of ... </p>
> <p> Eh già</p>

E' possibile selezionare anche _pseudo-elementi_ e _pseudo-classi_ (`::` alcuni anche con `:`):

- `a:link`
- `a:visited`
- `:focus`
- `:hover`
- `:active`
- `:checked`
- `::fist-letter`
- `::first-line`
- `::first-child`
- `::nth-child`
- `::last-child`

### 2.2.4. Selettori di Contesto

Permette di selezionarre elementi in base ai loro genitori, figli o fratelli.

<div class="flexbox" markdown="1">

|     Selettore      |                             Match                             | Esempio  |
| :----------------: | :-----------------------------------------------------------: | :------: |
|    Discendente     |        Contenuto da qualche parte all'interno del tag         | `div p`  |
|       Figlio       |              Figlio diretto del tag specificato               | `div>h2` |
| Fratello Adiacente | Specifica il tag direttamente successivo a quello specificato |  `h3+p`  |
| Fratello Generale  |     Elemento che ha lo stesso padre di quello specificato     |  `h3~p`  |

</div>

```html
<head>
  <style>
    ul a:link {
      color: blue;
    }

    ul a:hover {
      color: yellow;
    }
    #main time {
      color: red;
    }
    #main > time {
      color: purple;
    }
    #main div p:first-child {
      color: green;
    }
  </style>
</head>

<body>
  <nav>
    <ul>
      <li><a href="#">Canada</a></li>
      <li><a href="#">Germany</a></li>
      <li><a href="#">United States</a></li>
    </ul>
  </nav>
  <div id="main">
    Comments as of <time>2016-12-25</time>
    <div>
      <p>By Ricardo on <time>2016-05-23</time></p>
      <p>Easy on the HDR buddy.</p>
    </div>
    <hr />
    <div>
      <p>By Susan on <time>2016-11-18</time></p>
      <p>I love Central Park.</p>
    </div>
    <hr />
  </div>
  <footer>
    <ul>
      <li><a href="#">Home</a> |</li>
      <li><a href="#">Browse</a> |</li>
    </ul>
  </footer>
</body>
```

> <style>
>    ul.s a:link {color: blue;}
>    ul.s a:hover {color: yellow;}
>    #main time {color: red;}
>    #main>time{color:purple;}
>    #main .div p:first-child{color: green;}
> </style>
> <body>
>     <nav>
>         <ul class="s">
>             <li><a href="#">Canada</a></li>
>             <li><a href="#">Germany</a></li>
>             <li><a href="#">United States</a></li>
>         </ul>
>     </nav>
>     <div class=".div" id="main">
>         Comments as of <time>2016-12-25</time>
>         <div class=".div">
>             <p>By Ricardo on <time>2016-05-23</time></p>
>             <p>Easy on the HDR buddy.</p>
>         </div>
>         <hr/>
>         <div class=".div">
>             <p>By Susan on <time>2016-11-18</time></p>
>             <p>I love Central Park.</p>
>         </div>
>         <hr/>
>         </div>
>         <footer>
>         <ul class="s">
>             <li><a href="#">Home</a> | </li>
>             <li><a href="#">Browse</a> | </li>
>         </ul>
>     </footer>
> </body>

## 2.3. **Interazione tra gli stili**

Quando sono presenti tante regole è facile che accada che diverse regole vadano in conflitto.

Il CSS utilizza il seguente _principio di cascata_ per risolvere i conflitti:

1. <a href="#ereditarietà">Ereditarietà</a>
1. <a href="#specificità">Specificità</a>
1. <a href="#posizione">Posizione</a>

### 2.3.1. _Ereditarietà_

Molte proprietà CSS hanno effetto su un elemento e su i suoi discendenti.
Alcune proprietà che sono ereditate sono:

- Font
- Color
- List
- Text Proprietes

Altre non ereditate automaticamente sono:

- Layout
- Sizing
- Border
- Background
- Spacing

Tuttavia anche quest'ultime possono essere ereditate tramite _keyword_ `inherit`

```html
<style>
  div {
    font-weight: bold;
    margin: 5px;
    border: 1pt solid green;
  }
  div p:first-child {
    border: inherit;
    margin: inherit;
  }
</style>

<h3>Reviews</h3>
<div>
  <p>By Ricardo on <time>September 15, 2012</time></p>
  <p>Easy on the HDR buddy.</p>
</div>
<hr />

<div>
  <p>By Susan on <time>October 1, 2012</time></p>
  <p>I love Central Park.</p>
</div>
<hr />
```

>  <style>
>     .div {
>         font-weight: bold;
>         margin: 5px;
>         border: 1pt solid green;
>     }
>     .div p:first-child {
>         border: inherit;
>         margin: inherit;
>     }
> </style>
> <body>
>     <h3>Reviews</h3>
>     <div class="div">
>         <p>By Ricardo on <time>September 15, 2012</time></p>
>         <p>Easy on the HDR buddy.</p>
>     </div>
>     <hr/>
>     <div class="div">
>         <p>By Susan on <time>October 1, 2012</time></p>
>         <p>I love Central Park.</p>
>     </div>
>     <hr/>
> </body>

### 2.3.2. _Specificità_

Quando ci sono più regole per un determinato elemento, il browser applicherà quella più **specifica**.

Una semplice scala in ordine crescente è la seguente:

1. `body`
2. `div`, `article`, `main`, `aside`, `footer`
3. `p`, `pre`
4. Selettori di Classe
5. Selettori di ID

Un algoritmo che calcola la specificità è il seguente:

- 1 se `style` è inline, altrimenti 0 ($a$)
- Conta il numero di attributi ID ($b$)
- Conto il numero di attributi e pseudoclassi ($c$)
- Conto il numero di nomi di elementi e pseudoelementi nel selettore ($d$)

Il valore di specificità è data dal numero $dcba$.

<img src="./images/Specificita algoritmo.png">

```html
<style>
  div {
    font-weight: normal;
    color: magenta;
  }
  p {
    color: green;
  }
  .last {
    color: blue;
  }
  #verylast {
    color: orange;
    font-size: 16pt;
  }
</style>
<body>
  This text is not within a p element.
  <p>Reviews</p>
  <div>
    <p>By Ricardo on <time>September 15, 2012</time></p>
    <p>Easy on the HDR buddy.</p>
    This text is not within a p element.
  </div>
  <hr />
  <div>
    <p>By Susan on <time>October 1, 2012</time></p>
    <p>I love Central Park.</p>
  </div>
  <hr />

  <div>
    <p class="last">By Dave on <time>October 15, 2012</time></p>
    <p class="last" id="verylast">Thanks for posting.</p>
  </div>
  <hr />
</body>
```

> <style>
>     .body {
>         font-weight: bold;
>         color: red;
>     }
>     .div {
>         font-weight: normal;
>         color: magenta;
>     }
>     .ss {
>         color: green;
>     }
>     .last {
>         color: blue;
>     }
>     #verylast {
>         color: orange;
>         font-size: 16pt;
>     }
> </style>
> <div class=".body">
>     This text is not within a p element.
>     <p><span class="ss">Reviews</span></p>
>     <div class=".div">
>         <p><span class="ss">By Ricardo on <time>September 15, 2012</time></span></p>
>         <p><span class="ss">Easy on the HDR buddy.</span></p>
>         This text is not within a p element.
>     </div>
>     <hr/>
>     <div class=".div">
>         <p><span class="ss">By Susan on <time>October 1, 2012</time></span></p>
>         <p><span class="ss">I love Central Park.</span></p>
>     </div>
>     <hr/>
>     <div class=".div">
>         <p class="last">By Dave on <time>October 15, 2012</time></p>
>         <p class="last" id="verylast">Thanks for posting.</p>
>     </div>
>     <hr/>
> </div>

### 2.3.3. _Posizione_

Il principio di locazione viene utilizzato quando la specificit di due elementi è uguale.

L'ordine di locazione è questo:

1. Specifica _inline_
2. Specifica _embedded_
3. Specifica _author created_ (_linked_)
4. Specifica _user_
5. Specifica _browser_

Una proprietà può essere markata come `!important` è sovrascriverà tutte le altre.

## 2.4. **Modello Box**

In CSS, tutti gli elementi HTML sono esistono in un _elemento box_

<img src="./images/Modello Box.png" width="50%">

### 2.4.1. _Background_

Il _background_ di un elemento lo riempie fino al bordo. <br>
Esistono diverse proprietà per un elemento di background:

- `background-image: url(image)`
- `background-repeat:`
  - `repeat`
  - `no-repeat`
  - `repeat-y`
  - `repeat-x`
- `background-position: xAxis yAxis`

E' possibile concatenarle:

```css
.el {
  background: red url(.images/foto.jpg);
}
```

### 2.4.2. _Border_, _Margin_ e _Padding_

Con le proprietà `border`, `margin`, `padding` esistono forme lunghe e ridotte per settarli:

```css
img {
  border-top-color: red; /* Solo il lato superiore */
  border-right-color: green; /* Solo il lato a destra */
  border-bottom-color: yellow; /* Solo il lato inferiore */
  border-left-color: blue; /* Solo il lato a sinistra */
  border-color: red; /* Tutti i lati con lo stesso colore*/
  border-color: red green orange blue; /* Tutti e 4 con colori diversi */
}
```

Per quanto riguarda `margin` e `padding` se sono presenti uno dopo l'altro è possibile che collassino uno nell'altro.
Il CSS quando due margini <u>verticali</u> si toccano, essi collassano:

- Viene rappresentato il più grande
- Il più piccolo viene messo a 0

I margini orizzontali invece <u>non collassano **mai**</u>.
Ci sono tuttavia dei casi dove anche i margini verticali non collassano.

### 2.4.3. `width` e `height`

La larghezza e l'altezza totale di un elemento è uguale alla somma tra il suo `padding`, i suoi `border` e i suoi `margin`.

Per settare questi valori si possono usare:

- `px`: sono fissi ma c'è il rischio che l'elemnto "sfori" la pagina
- `%`: le dimensioni sono relativi al tag genitore dell'elemento
- `em`: le dimensioni sono relative al testo all'interno

Per regolare i bordi è possibile utilizzare i _Developer Tools_ dei browser.

```html
<style>
  html,
  body {
    margin: 0;
    width: 100%;
    height: 100%;
    background: silver;
  }
  .pixels {
    width: 200px;
    height: 50px;
    background: teal;
  }
  .percent {
    width: 50%;
    height: 50%;
    background: olive;
  }
  .parentFixed {
    width: 400px;
    height: 150px;
    background: beige;
  }
  .parentRelative {
    width: 50%;
    height: 50%;
    background: yellow;
  }
</style>
<body>
  <div class="pixels">Pixels - 200px by 50 px</div>
  <div class="percent">Percent - 50% of width and height</div>
  <div class="parentFixed">
    <strong>parent has fixed size</strong>
    <div class="percent">PERCENT - 50% of width and height</div>
  </div>
  <div class="parentRelative">
    <strong>parent has relative size</strong>
    <div class="percent">PERCENT - 50% of width and height</div>
  </div>
</body>
```

> <style>
>     .pixels {
>         width:200px;
>         height:50px;
>         background: teal;
>     }
>     .percent {
>         width:50%;
>         height:50%;
>         background: olive;
>     }
>     .parentFixed {
>         width:400px;
>         height:150px;
>         background: beige;
>         color: black;
>     }
>     .parentRelative {
>         width:50%;
>         height:50%;
>         background: yellow;
>         color: black;
>     }
> </style>
> <body>
>     <div class="pixels">
>         Pixels - 200px by 50 px
>     </div>
>     <div class="percent">
>         Percent - 50% of width and height
>     </div>
>     <div class="parentFixed">
>         <strong>parent has fixed size</strong>
>         <div class="percent">
>            PERCENT - 50% of width and height
>         </div>
>      </div>
>      <div class="parentRelative">
>         <strong>parent has relative size</strong>
>         <div class="percent">
>            PERCENT - 50% of width and height
>         </div>
>      </div>
> </body>

## 2.5. **Stili di Testo**

Il CSS fornisce due tipi di proprietà per i testi:

- **font properties**: influenza il font
- **paragraph properties**: influenza il testo indipendentemente dal font

E' possibile inserire più font per un testo, il CSS lo interpreterà con ordine di preferenza nel caso in cui non riesca a trovare uno degli stili.

```css
p {
  font-family: Cambria, Georgia, "Times New Roman", serif;
}
```

I browser possono utilizzare tutti i font installati in un calcolatore, tuttavia non hanno accesso diretto a tutti i font online.

Esiste tuttavia un _web font stack_ supportato dal selettore `@font-face`.

Il text styling sono una serie di proprietà che modifica le proprietà del testo, alcuni esempi sono:

- `letter-spacing`
- `line height`
- `text-align`
- `text-shadow`

Per quanto riguarda i `font-size` si utilizzano le unità relative `em` e **percentuali**, entrabe relative al loro elemento padre.
In CSS3 esiste l'unità `rem`, che è relativa alla radice (l'elemento `<html>`)

```html
<style>
  body {
    font-size: 100%;
  }
  h4 {
    font-size: 1.125em;
  } /* 1.25 x 16 = 18 */
  h3 {
    font-size: 1.5em;
  } /* 1.5 x 16  = 24 */
  h2 {
    font-size: 2em;
  } /* 2 x 16 = 32 */
  p {
    font-size: 1rem;
  }
</style>
<body>
  <p>this will be about 16 pixels</p>
  <h2>this will be about 32 pixels</h2>
  <h3>this will be about 24 pixels</h3>
  <h4>this will be about 18 pixels</h4>
  <p>this will be about 16 pixels</p>
</body>
```

> <style>
>     .h4 { font-size: 1.125em; }  /* 1.25 x 16 = 18 */
>     .h3 { font-size: 1.5em; }    /* 1.5 x 16  = 24 */
>     .h2 { font-size: 2em; }      /* 2 x 16 = 32 */
>     .pt {font-size: 1rem; }
> </style>
> <p class="pt">this will be about 16 pixels</p>
> <h2 class="h2">this will be about 32 pixels</h2>
> <h3 class="h3">this will be about 24 pixels</h3>
> <h4 class="h4">this will be about 18 pixels</h4>
> <p class="pt">this will be about 16 pixels</p>

---

# 3. **CSS Avanzato: _Layout_**

Ogni elemento blocco di una pagina è caratterizzato da un certo tipo di _flow_ che rappresenta come gli elementi al suo interno vengono visualizzati.

Il **Normal Flow** si riferisce a come il browser rappresenta i tag, dividendoli in:

- Elementi `block-level`: `p`, `div`, `h2`, `ul`, `table`, ...
- Elementi `inline`: `em`, `a`, `img`, `span`, ...

<img src="./images/Advanced CSS/Normal Flow.png">

E' tuttavia possibile cambiare se un elemento deve essere visualizzato come `block` o come `inline`.
La regola che modifica ciò è la `display`

```css
span {
  display: block;
}

li {
  display: inline;
}
```

## 3.1. **Grid Layout**

Il layout a griglia è potente, personalizzabile e incredibilmente facile da usare.

Ogni blocco figlio in un contenitore all'interno di un genitore con `display: grid`, verrà inserito in una griglia.

Per creare più colonne si utilizza la specifica `grid-template-columns` anche tramite l'unità di misura `fr` (_fraction_).  
Per velocizzare è possibile utilizzare la funzione `repeat()`, che ripete il pattern.

```css
.container {
  display: grid;
  gap: 10px; /* gap tra due righe*/
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-columns: 80px 30px 50px;
}
```

```html
<div class="container">
  <div>1</div>
  <div>2</div>
  <div>3</div>
  <div>4</div>
  <div>5</div>
  <div>6</div>
</div>
```

> <style>
>    .container{
>    display: grid;
>    gap: 10px;
>    grid-template-columns: 1fr 1fr 1fr;
>    grid-template-columns: 80px 30px 50px;
> }

    .container div {
        background-color: red;
        color
    }

> </style>
>
> <div class="container">
>    <div>1</div>
>    <div>2</div>
>    <div>3</div>
>    <div>4</div>
>    <div>5</div>
>    <div>6</div>
> </div>

Nel caso in cui volessimo riempire tutto lo spazio possibile o la maggior parte di esso si utilizza la funzione:

```css
grid-template-columns: repeat(auto-fill, minmax(..., ...))
grid-template-columns: repeat(auto-fit, minmax(..., ...))
```

```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
}

.container span {
  display: block;
}

.a {
  grid-column-start: 1;
  grid-column-end: 3;
  /*
    * Uguale a
    * grid-column: 1/3;
    * grid-column: 1/span 2;
    */
}

.b {
  grid-row: 2;
  grid-column: 2;
}
```

```html
<div class="container">
  <span class="a">1</span>
  <span class="b">2</span>
  <span>3</span>
  <span>4</span>
  <span>5</span>
  <span>6</span>
</div>
```

> <style>
>    .containerdiv {
>    display: grid;
>    grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
>    }
>
>    .container span {
>        display: block;
>    }
>
>    .b11{
>    grid-row: 2;
>    grid-column: 2;
>    }
>
>    .a11{
>        grid-column-start: 1;
>        grid-column-end: 3;
>    }
> </style>
>
> <div class="containerdiv">
>    <span class="a11">1</span>
>    <span class="b11">2</span>
>    <span>3</span>
>    <span>4</span>
>    <span>5</span>
>    <span>6</span>
> </div>

Le celle nei disponimenti a griglia hanno delle proprietà che controllano l'allineamento dei contenuti.

<img src="./images/Advanced CSS/grid-align.png">

Esiste un ulteriore voce chiamata `grid-template-areas`, che permette di esplicitare la disposizione degli elementi all'iterno di una griglia:

```css
.container {
  grid-gap: 10px;
  display: grid;
  grid-template-rows: 100px 150px 100px;
  grid-template-columns: 75px 1fr 1fr 1fr 1fr;
  color: black;
  grid-template-areas:
    ".. a1 a2 a3 a4"
    "b1 b2 b2 b2 b3"
    "b1 c1 c2 c2 c2";
}
.a1 {
  grid-area: a1;
}
.a2 {
  grid-area: a2;
}
.a3 {
  grid-area: a3;
}
.a4 {
  grid-area: a4;
}
.b1 {
  grid-area: b1;
}
.b2 {
  grid-area: b2;
}
.b3 {
  grid-area: b3;
}
.c1 {
  grid-area: c1;
}
.c2 {
  grid-area: c2;
}

.yellow {
  background-color: yellow;
}
.orange {
  background-color: orange;
}
.cyan {
  background-color: cyan;
}
```

```html
<section class="container">
  <div class="yellow a1">A1</div>
  <div class="yellow a2">A2</div>
  <div class="yellow a3">A3</div>
  <div class="yellow a4">A4</div>
  <div class="orange b1">B1</div>
  <div class="orange b2">B2</div>
  <div class="orange b3">B3</div>
  <div class="cyan c1">C1</div>
  <div class="cyan c2">C2</div>
</section>
```

> <style>
> .container22 {
>   grid-gap: 10px;
>   display: grid;
>   grid-template-rows: 100px 150px 100px;
>   grid-template-columns: 75px 1fr 1fr 1fr 1fr;
>   color: black;
>   grid-template-areas: ". a1 a2 a3 a4"
>   "b1 b2 b2 b2 b3"
>   "b1 c1 c2 c2 c2";
> }
> .a122 { grid-area: a1; }
> .a222 { grid-area: a2; }
> .a322 { grid-area: a3; }
> .a422 { grid-area: a4; }
> .b122 { grid-area: b1; }
> .b222 { grid-area: b2; }
> .b322 { grid-area: b3; }
> .c122 { grid-area: c1; }
> .c222 { grid-area: c2; }
>
> .yellow{ background-color: yellow;}
> .orange{ background-color: orange;}
> .cyan{ background-color: cyan;}
> </style>
> <section class="container22">
>   <div class="yellow a122">A1</div>
>   <div class="yellow a222">A2</div>
>   <div class="yellow a322">A3</div>
>   <div class="yellow a422">A4</div>
>   <div class="orange b122">B1</div>
>   <div class="orange b222">B2</div>
>   <div class="orange b322">B3</div>
>   <div class="cyan c122">C1</div>
>   <div class="cyan c222">C2</div>
> </section>

## 3.2. **Posizione degli elementi**

E' possibile spostare un oggetto dalla sua posizione di base nel _normal flow_ tramite la proprietà `position`.

<div class="flexbox" markdown="1">

| Valore `position` |                                                                                    Descrizione                                                                                    |
| :---------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|    `absolute`     |                                   L'elemento viene rimosso dal flusso normale e posizionato in relazione al suo antenato posizionato più vicino                                   |
|      `fixed`      |                                        L'elemento è fissato in una posizione specifica nella finestra anche quando si scorre il documento                                         |
|    `relative`     | L'elemento viene spostato rispetto a dove sarebbe nel flusso normale.<br> Gli altri elementi fanno riferimento al valore originale di `position` e quello spazio viene mantenuto. |
|     `static`      |                                          (`default`) L'elemento è posizionato in base al flusso normale. Questo è il valore predefinito                                           |

</div>

Rimane la possibilità di avere immagini che si sovrappongano, perciò esiste la proprietà `z-index` per far si che <u>elementi posizionati</u> vengano mostrati sopra o sotto altri.  
La proprietà è sempre **relativa al suo contenitore, <u>non è assoluta</u>**

---

## 3.3. **Elementi fluttuanti** (`float`)

E' possibile muovere un elemento dalla sua posizione nel _flow normale_ tramite la proprietà `float`.

<div class="flexbox" markdown="1">

| Valore  |                                                       Descrizione                                                        |
| :-----: | :----------------------------------------------------------------------------------------------------------------------: |
| `left`  | L'elemento viene messo alla sinistra del suo contenitore.<br> Altri elementi adiacenti sono posizionati sulla sua destra |
| `right` | L'elemento viene messo alla destra del suo contenitore. <br>Altri elementi adiacenti sono posizionati sulla sua sinistra |
| `none`  |                        L'elemento può avere altri elementi adiacenti sia a sinistra che a destra                         |

</div>

L'elemento che ha la proprietà `float` deve <u>sempre avere la sua `width` specificata</u>, così da dare informazioni sul punto di adiacenza al resto della pagina.

Se sono presenti più elementi in prossimità tra di loro, ogni elemento viene posizionato rispetto al _floating_ precedente e all'altezza relativa degli elementi precedenti.  
Per imporre di non avere più un `float` relativo si può usare la proprietà `clear: left/right`.

<img src="./images/Advanced CSS/Float.png">

Un altro problema comune con i gli elementi _floating_ è quello di blocchi che contengono **solo** elementi _floating_, in quanto il blocco essenzialmente sparisce.  
Per ovviare a questo problema:

- Si rende il blocco `float` (non sempre possibile)
- Si utilizza la proprietà `overflow: auto`.

<img src="./images/Advanced CSS/Overflow.png">

E' possibile inoltre creare dei **contesti di posizionamento** per ottenere risultati visili migliori.  
Per fare ciò basta riferire il blocco come `relative`.  
Questo è utile per:

- Inserire immagini in _overlay_ sopra altre immagini
- Nascondere e mostrare immagini secondo una scelta

Per nascondere gli elementi esistono due modi principali:

- `display: none`: nasconde l'elemento e si comporta come se non esistesse.
- `visibility: hidden`: nasconde l'elemento ma il resto della pagina si comporta come se fosse ancora lì.

In combinazione alla pseudoclasse `:hover`, la proprietà `visibility` può essere usata per ottenere una verisone più grande di un immagine.

```css
figcaption.popup {
  padding: 10px;
  background: #e1e1e1;
  position: absolute;

  -webkit-box-shadow: 0 0 15px #a9a9a9;
  -moz-box-shadow: 0 0 15px #a9a9a9;
  box-shadow: 0 0 15px #a9a9a9;

  visibility: hidden;
}

figure.thumbnail:hover figcaption.popup {
  position: absolute;
  top: 0;
  left: 100px;
  visibility: visible;
  color: black;
}
```

```html
<figure class="thumbnail">
  <img src="immagine.jpg" />
  <figcaption class="popup">
    <img src="immagine.jpg" />
    <p>Ajeje Brazorf</p>
  </figcaption>
</figure>
```

> <style>
>    figcaption.popup{
>    padding: 10px;
>    background: #e1e1e1;
>    position: absolute;
>
>    -webkit-box-shadow: 0 0 15px #A9A9A9;
>    -moz-box-shadow: 0 0 15px #A9A9A9;
>    box-shadow: 0 0 15px #A9A9A9;
>
>    visibility: hidden;
>    }
>
>    figure.thumbnail:hover figcaption.popup{
>        position: absolute;
>        top: 0;
>        left: 100px;
>        visibility: visible;
>        color: black;
>    }
>   figure.thumbnail{
>       all: initial;
>   }
>   figure.thumbnail img{
>       all = initial;
>   }
> </style>
>
> <figure class="thumbnail">
>    <img src="./images/Advanced CSS/ajejeBrazorf.jpg">
>    <figcaption class="popup">
>        <img src="./images/Advanced CSS/ajejeBrazorf.jpg">
>        <p>Ajeje Brazorf</p>
>    </figcaption>
> </figure>

---

## 3.4. **Layout Multicolonna**

Non esistono modi semplici per creare pagine con layout multicolonna, poiché ci sono dei vantaggi/svantaggi per ogni approccio:

- Usare `float`
- Usare `positioning`

### 3.4.1. _Float Approach_

Con l'_approccio float_ i principali problemi sono dati dall'assenza di `padding` e `border` tra i contenuti float e non.  
Una tecnica è quella di modificare il marigne sinistro del contenutore della schermata, affinché nel luogo dove il _float_ arriva la pagina è vuota.

Alcuni esempi di pagine possono essere questi:

<div class="grid2">
<div>
<img class="80" src="./images/Advanced CSS/Float approach.png">
</div>
<div>
<img class="80" src="./images/Advanced CSS/Float approach 1.png">
</div>
</div>

### 3.4.2. _Positioning Approach_

Anche la proprietà `positioning` può essere utilizzata per ottenere layout multicolonna.  
In genere questo approccio è `absolute` rispetto agli elementi _float_.

<img class="75" src="./images/Advanced CSS/Position Approach.png">

Una differenza rispetto all'approccio precedente è il fatto che nel caso di elementi molto grandi, il `position: absolute` lo rimuove dal flusso, rischiando la sovrapposizione con altri elementi.

<img class="75" src="./images/Advanced CSS/Position Approach Problem.png">

### 3.4.3. _Flexbox Approach_

<style>
    img {
        width:35%;
    }
    .div222{
        display: flex;
        justify-content: space-around;
    }
    .img {
        position:relative;
        left:50%;
        transform: translateX(-50%);
        width:40%;
    }
</style>

E' un meccanismo CSS che risolve i problemi di _positioning_ e _float_, infatti produce codice molto generalizzato e riutilizzabile.

Le proprietà del **blocco contenitore**:

<div class="grid2">
<img class="75" src="./images/Advanced CSS/flex/align-items.png">
<img class="75" src="./images/Advanced CSS/flex/justify-content.png">
<img class="75" src="./images/Advanced CSS/flex/frex-wrap.png">
<img class="75" src="./images/Advanced CSS/flex/flex-direction.png">
</div>

Le proprietà dell'**elemento contenuto**:

<img src="./images/Advanced CSS/Flex/flex.png">

## 3.5. **Layout CSS**

Uno dei problemi del web design è la grande varietà di schermi sulle quali le pagine si vede, rendendo inutilizzabile la mera scalatura.

Alcuni approcci utilizzati sono:

- _Fixed Layout_
- _Liquid Layout_
- _Hybrid Layout_

### 3.5.1. _Fixed Layout_

La larghezza del design è settata dallo sviluppatore, e rappresenta la **larghezza ideale** basata su un "monitor tipico".

Questo approccio è facile da effettuare e genericamente ha un output visivo prevedibile.

Ha tutta via degli svantaggi:

- Per gli schermi grandi si richia di avere **tanto** spazio bianco
- Per gli schermi più piccoli si perde parte di pagina

### 3.5.2. _Liquid Layout_

Le dimensioni di ogni elemento le larghezze sono specificate **in percentuale**, in maniera che la pagina possa essere visibile su _qualsiasi schermo_.

Tuttavia anche qui ci sono degli svantaggi:

- Per schermi troppo grandi: il testo risulta di difficile lettura e potrebbe interfacciarsi male con gli elementi di dimensione fissata
- Per schermi troppo piccoli: gli elementi diventano troppo piccoli per poter essere visibili

### 3.5.3. _Hybrid Layout_

E' un ibrido tra il _liquid_ e il _fixed_, a seconda dello spazio a disposizione.

In generale questo layout applica il seguente layout:

- _Sidebar_ $\rightarrow$ fixed
- _Main_ $\rightarrow$ liquid

Anche qui si possono riscontrare problemi, perciò si utilizza un **Responsive Design**

---

## 3.6. **Responsive Design**

In questo design la pagina "risponde" ai cambiamenti delle dimensioni del browser in maniera diversa rispetto al _liquid layout_.

In un _responsive layout_, le immagini sono scalate e gli elementi di navigazione sono rimpiazzati/spostati in proporzione al rimpicciolimento della scheda del browser.

Ci sono quattro componenti chiave che permettono ai _responsive layout_ di funzionare:

1. _Liquid Layout_
1. Effettuare **scaling** sulle immagini <u>rispetto al _viewport_</u>
1. Settare il _viewport_ **in modo esplicito**, attraverso il tag **&lt;meta&gt;**
1. Personalizzare il CSS per _viewport_ diversi, utilizzando delle _media queries_

Scalare le immagini è un qualcosa abbastanza semplice, basta impostare la seguente regola:

<p style="text-align: center; font-family: monospace">max-width:100%;</p>

Per siti _responsive_ che scalano per entrare in uno schermo più piccolo, la pagina web può **chiedere al browser del cellulare la sua viewport**, per poi utilizzarla.  
Per fare ciò si utilizza il seguente tag nella sezione **&lt;head>** del documento:

<p style="text-align: center; font-family: monospace">&lt;meta name="viewport" content="width=device-width"&gt;</p>

Con questo tag il browser dei cellulari renderizza la pagina sul proprio viewport, impostando la dimensione in pixel del dispositivo uguale ad esso.

### 3.6.1. _Media Queries_

Un altro componente fondamentale dei _responsive design_ sono le **CSS media queries**.  
Le _media queries_ sono un modo di applicare delle regole di stile <u>solo</u> quando certe regole sono rispettate.  
Per ottenere delle regole applicabili solo su dispositivi con larghezza ridotta inseriamo la seguente stringa nel **CSS**:

```css
@media only screen and (max-width: 480px) {
  /*...*/
}
```

In questa stringa:

- _only_: imposta che tutte le condizioni devono essere vere
- _screen_: il dispositivo deve essere uno schermo

La norma prevede di inserire le _media queries_ secondo l'apporccio del **miglioramento progressivo**:

- Telefoni
- Tablet
- Desktop

Altri attributi delle _media queries_ sono:

<div class="flexbox" markdown="1">

|    _Feature_    |                          _Description_                          |
| :-------------: | :-------------------------------------------------------------: |
|     `width`     |                   Larghezza della _viewport_                    |
|    `height`     |                    Altezza della _viewport_                     |
| `device-width`  |                    Larghezza del dispositivo                    |
| `device-height` |                     Altezza del dispositivo                     |
|  `orientation`  | Se il dispositivo è in visualizzazione _portrait_ o _landscape_ |
|     `color`     |                    Numero di bit per colore                     |

</div>

Quando si tratta di immagini può utilizzare anche il tag `<picture>`, inserendo al suo interno più `<source>` da utilizzare in base al contesto nel quale il sito è aperto:

```html
<picture>
  <source media="(min-width:960px)" srcset="large.jpg" />
  <source media="(min-width:480px)" srcset="medium.jpg" />
  <source srcset="small.jpg" />
</picture>
```

#### 3.6.1.1. _Menù_

```css
.menu {
  display: flex;
  flex-direction: row;
  list-style: none;
  padding: 0;
  margin: 0;
}

.menu-item {
  flex: 1;
  text-align: center;
  padding: 0.5em;
}

@media (max-width: 600px) {
  .menu {
    flex-direction: column;
  }
  .menu-item {
    flex: none;
    width: 100%;
  }
}
```

```html
<ul class="menu">
  <li class="menu-item">Voce</li>
  <li class="menu-item">Voce</li>
  <li class="menu-item">Voce</li>
  <li class="menu-item">Voce</li>
</ul>
```

> <style>
> .menu {
>    display:flex;
>    flex-direction: row;
>    list-style: none;
>    padding: 0;
>    margin: 0;
> }
>
> .menu-item{
>    flex: 1;
>    text-align: center;
>    padding: 0.5em;
> }
>
> @media (max-width: 600px){
>    .menu{
>        flex-direction: column;
>    }
>    .menu-item{
>        flex: none;
>        width: 100%;
>    }
> }
> </style>
> <ul class="menu">
>    <li class="menu-item">Voce 1</li>
>    <li class="menu-item">Voce 2</li>
>    <li class="menu-item">Voce 3</li>
>    <li class="menu-item">Voce 4</li>
> </ul>

## 3.7. **Filtri, Transizioni e Animazioni**

Il CSS ci permette di applicare una proprietà `filter`

```css
#someImage {
  filter: grayscale(100%);
  /*Chrome e Opera*/
  -webkit-filter: grayscale(100%);
}

#anotherImage {
  filter: blur(5px) hue-rotate(60deg) saturate(2);
  /*Chrome e Opera*/
  -webkit-filter: blur(5px) hue-rotate(60deg) saturate(2);
}
```

E' inoltre possibile inserire transizioni tra gli stati dei diversi oggetti nella pagina.  
Per fare ciò esiste una famiglia di attributi `transition`:

- `transition-propery`: Quale proprietà cambia nel tempo
- `transition-duration`: Durata della transizione
- `transition-timing-function`: `linear`, `ease-out`, `ease-in`
- `transition-delay`: dopo quanto tempo la transizione inizia

```css
button {
  background-color: green;
  color: black;
  transition-property: background-color, color;
  transition-duration: 0.5s;
  transition-timing-function: ease-out;
  transition-delay: 0s;
}

button:hover {
  background-color: red;
  color: white;
}
```

```html
<button>Bottone</button>
```

> <style>
>    .button {
>        background-color: green;
>        color: black;
>        transition-property: background-color, color;
>        transition-duration: 0.5s;
>        transition-timing-function: ease-out;
>        transition-delay: 0s;
>    }
>
>    .button:hover{
>        background-color: red;
>        color: white;
>    }
> </style>
>
> <button class="button">Bottone</button>

E' inoltre possibile inserire delle animazioni negli oggetti.  
Le animaizoni non necessitano un _trigger_, e possono essere messe in loop.

```css
p {
  animation-name: slideIn;
  position: absolute;

  left: 2.5%;
  animation-play-state: running;
  animation-duration: 3s;
  animation-delay: 1s;
  animation-iteration-count: 1;
  animation-timing-function: linear;
  transform: translate(-50%, -50%);
  animation-fill-mode: forwards;
}

p:hover {
  animation-play-state: paused;
}

@keyframes slideIn {
  0% {
    left: 2.5%;
    top: 2.5%;
  }

  50% {
    left: 25%;
    top: 25%;
  }

  100% {
    margin: 0%;
    padding: 0%;
    left: 50%;
    top: 50%;
  }
}
```

```html
<p class="animated">Animata</p>
```

> <style>
>    .pipo {
>    animation-name: slideIn;
>    position: absolute;
>
>    left: 2.5%;
>    animation-play-state: running;
>    animation-duration: 3s;
>    animation-delay: 1s;
>    animation-iteration-count: 1;
>    animation-timing-function: linear;
>    transform: translate(-50%, -50%);
>    animation-fill-mode:forwards;
> }
>
>    .pipo:hover{
>        animation-play-state: paused;
>    }
>
>    @keyframes slideIn {
>
>        0% {
>            left: 2.5%;
>            top:2.5%;
>        }
>
>        50%{
>            left: 25%;
>            top:25%;
>        }
>
>        100%{
>            margin: 0%;
>            padding:0%;
>            left: 50%;
>            top: 50%;
>        }
>    }
> </style>
>
> <p class="pipo animated">Animata</p>

