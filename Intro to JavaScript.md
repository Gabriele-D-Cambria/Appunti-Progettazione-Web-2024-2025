---
title: Intro to JavaScript
---

# 1. Index

<!--toc:start-->

- [1. Index](#1-index)
- [2. Javascript](#2-javascript)
  - [2.1. Utilizzo di JS](#21-utilizzo-di-js)
  - [2.2. Variabili](#22-variabili)
  - [2.3. Output](#23-output)
  - [2.4. Oggetti Built-In](#24-oggetti-built-in)
  - [2.5. Stringhe e Concatenazione](#25-stringhe-e-concatenazione)
  - [2.6. Condizioni](#26-condizioni)
  - [2.7. Operatori bit-a-bit](#27-operatori-bit-a-bit)
  - [2.8. Cicli](#28-cicli)
  - [2.9. Gestione Eccezioni](#29-gestione-eccezioni)
  - [2.10. Array e iteratori](#210-array-e-iteratori)
  <!--toc:end-->

# 2. Javascript

Javascript è un linguaggio _object-oriented_ e _dyanmically typed_.  
E' un linguaggio creato ed utilizzato per applicazione _client-side_.

E' un linguaggio a tipizzazione debole derivato dal C.  
A differenza di altri linguaggi _object-oriented_ le funzioni in javascript sono anch'esse **oggetti**.

E' un linguaggio a <u>flusso di esecuzione singolo</u> nel quale le variabili possono essere facilmente (persino in maniera implicita) convertite da un _datatype_ ad un altro.

Nonostante il nome sia molto simile a quello di _Java_, un altro linguaggio _object-oriented_, i due sono due cose completamente diverse.  
Le somiglianze nel nome sono dovute a fini puramente commerciali.

Javascript è stato introdotto da _Netscape_ nel 1996.  
L'anno dopo il linguaggio è stato affidato ad **ECMA**, perciò il nome **ECMAScript** sarebbe più corretto.  
La sesta edizione (**ES6**) è la versione che ha aggiunto la tante elementi al linguaggio (classi, iteratori, funzioni freccia e promesse).

Il codice Javascript è uno _script client-side_, ed è di fatti eseguito localmente dai browser.
Questo diminuisce il carico dei server e migliora i tempi di risposta a cambiamenti dei browser.
Alcune funzionalità del JS sono:

- Poter cambiare le proprietà di alcuni tag
- Generare pezzi di codice HTML nella nostra pagina

Tuttavia non è garantito che il client sia dotato di un interprete _JS_.  
E' inoltre estremamente difficile debuggare e mantenere il codice, inoltre gli errori fermano la sua esecuzione (a differenza di ciò che accade con HTML e CSS).  
JS è un linguaggio in continuo sviluppo, perciò è possibile avere dei problemi con browser non aggiornati.

Le richieste in Javascript hann una struttura del genere:

<img src="./images/JS/Javascript and Web 2.0.png">

Oggi nel _software development_ JS ha ampliato le sue funzionalità oltre i limiti dei browser:

- E' possibile utilizzarlo _server-side_ in ambienti come **Node.js**
- E' utilizzato da **MongoDS** come _query-language_
- **Adobe Creative Suite** e **Open Office** utilizzano JS come linguaggio _end-user_.

## 2.1. Utilizzo di JS

Come CSS, anche JS può essere introdotto in diversi modi:

- _Inline_: frammenti solitamente piccoli, codice associato direttamente a degli attributi degli elementi HTML
- _Embedded_: in un tag `<script>`
- _External_: si scrive in un file separato .js e linkato tramite il tag `<script>`

```html
<html lang="en">
  <head>
    <title>JS</title>
    <script>
      alert("Questo apparirà prima di tutto il resto");
    </script>

    <script src="fileJS.js"></script>
  </head>
  <body>
    <h1>Titolo</h1>
    <a href="JavaScript:OpenWindow();">Per più informazioni</a>
    <input type="button" onclick="alert('Sei sicuro?');" />

    <script>
      alert("Hello World!");
    </script>
  </body>
</html>
```

Ci possono essere infinite ragione per i quali si vuole disabilitare JS.  
Per interagire con l'utente e informarlo della scelta si utilizza il tag `<noscript>`

Gli script JS possono essere eseguiti in momenti diversi a seconda che sia:

- _Codice Globale_: eseguito quando incontrato nel render della pagina
- _Funzioni_: eseguito solo qualdo la funzione è chiamata
- _Eventi_: eseguito solo quando l'evento accade

Durante l'esecuzione del JS, i browser moderni _mettono in pausa il render HTML_.

## 2.2. Variabili

Le variabili sono **tipizzate dinamicamente**, ovvero non hanno un tipo specifivo.

Per dichiarare una variabile si utilizzano le _keyword_ `let`,`var` o `const`

```js
let x;
let foo = 0;
foo = 4;
foo = "hello";
```

Come in C, la dichiarazione e la definizione di una variabile possono essere successivi.

JS ha due basici _data types_:

- Tipi Primitivi
  - Boolean
  - Number (double-presicion 64bit floating point)
  - String
  - Null
  - Undefined
  - Symbol
- Tipi riferimento
  - Array
  - Oggetti

```js
// Tipi Primitivi
let abc = 27;
let def = "hello";

// Tipi Riferimento
let foo = [45, 35, 25];
let xyz = def;
let bar = foo;

bar[0] = 200;
// foo[0] è adesso uguale a 200
```

`const` si riferisce a variabili che **non cambiano il loro stato**.
Nel caso di variabili tipizzate ciò implica che non possano mai cambiare direttamente il loro valore.
Nel caso di variabili riferimento invece il è il valore del riferimento che non può cambiare, mentre il suo contenuto sì.

Se una variabile è dichiarata con `var` fuori da una funzione, qeusta variabile diventa una **proprietà dell'oggetto globale**

```js
var a = "ABC";
const b = "DEF";
let c = "XYZ";

console.log(this.a);
// ABC
console.log(this.b);
// Errore
console.log(this.c);
// Errore
```

Questo comportamento è formtemente sconsigliato, poiché in grandi script potremmo andare a sovvraffollare le proprietà del'oggetto globale, potendo anche creare casi di omonimia.

In JS è possibile utilizzare variabili che non sono **mai state dichiarate**.
L'interprete andrà a dichiarare in automatico quella variabile come **variabile globale** (_proprietà oggetto globale_).

```js
var abc = 10;
if (abc === 10) {
  dec = 20;
}
console.log(abc);
// 10
console.log(dec);
// 20
```

## 2.3. Output

Alcune funzioni per poter interagire con l'utente sono:

```js
alert(); // Finserta PopUp
prompt(); // Finestra popup con input field
confirm(); // PopUp con pulsanti di Ok e Cancel

document.write(); // Scrive direttamente sulla pagina HTML
/*! Solitamente non è da utilizzare
 *   Sono da preferire JavaScript DOM
 */

console.log(); // Scrive nella console nel broser (strumenti da amministratore del browser)
```

## 2.4. Oggetti Built-In

JS ha diversi oggetti che possono essere utilizzati in qualunque momento:

- Object
- Function
- Boolean
- Error
- Number
- Math
- Date
- String
- Regexp

Altri invece utilizzano oggetti che non sono parte del linguaggio in se per se, ma del contensto del browser:

- Conosle
- Window
- Document

```js
let def = new Date();

let abc = def.toString();
```

## 2.5. Stringhe e Concatenazione

Una stringa in JS è contenuta tra i caratteri `" "` oppure `' '`.
Per poter utilizzare i caratteri `"` e `'` all'interno della stringa, essi devono essere preceduti dal carattere _backslash_ `\` (che si precede se si vuole inserire) (`\"`, `\'`, `\\`)
Per combinare stringhe tra di loro si utilizza il carattere `+`.
Nel caso in cui si concatenano stringhe e numeri, quest'ultimi vengono convertiti in stringhe.

```js
const country = "France";
const city = "Paris";
const population = 67;
const count = 2;

let msg = city + " is the capital of " + country;
msg += " Population of " + country + " is " + population;

let msg2 = population + count;

console.log(msg);
//> Paris is the capital of France Population of France is 67

console.log(msg2);
//> 69
```

## 2.6. Condizioni

Le keyword per le condizioni in JS sono quasi identiche a quello del PHP, Java o C++.

Gli operatori comparativi in JS rispetto a C++ introducono:

- `===`: uguale nel valore e nel tipo
- `!==`: diverso nel valore o nel tipo

Esistono quindi le keyword `if`, `else`, `else if`, `switch` e persino **l'operatore ternario**.

I valori in JS sono tutti _truthy_, ovvero convertiti nel valore booleano `true`.
Le uniche eccezioni sono `false`, `0`, `NaN` e `undefined`.

Alcune regole particolari:

- `NaN != NaN`
- _Oggetti_, _funzioni_ e _Array_ sono uguali solo se si riferiscono allo stesso oggetto, indipendentemente dai valori contenuti nei due.
- `null === null`
- `undefined === undefined`
- `null == undefined` ma `null !== undefined`

```js
switch (artType) {
  case "PT":
    output = "Painting";
    break;
  case "SC":
    output = "Sculpture";
    break;
  default:
    output = "Other";
}
// equivalent
if (artType == "PT") output = "Painting";
else if (artType == "SC") output = "Sculpture";
else output = "Other";

// equivalent

output = artType == "PT" ? "Painting" : artType == "SC" ? "Sculpture" : "Other";
```

Se si prova a comparare tipi diversi l'interprete JS prova a convertirli in un tipo:

- Numero e stringa $\rightarrow$ `string(Numero)`
- Uno dei due è `true`/`false` $\rightarrow$ `1`/`0`
- Oggetto e stringa $\rightarrow$ `ogg.toString()` oppure `ogg.valueOf()`

Esiste anche l'operatore `typeOf` che ritorna una stringa contenentr il _tipo dell'operando_:

```js
let num1 = 3;
let num2 = 3.0;
let b = true;
let shape = "round";
typeof num1;
// 'number'
typeof num2;
// 'number'
typeof b;
// 'boolean'
typeof shape;
// 'string'
```

Un ulteriore operatore è l'operatore `void`, che permette di valutare espressioni _senza un valore di return_.

```html
<a href="javascript:void(document.body.style.backgroundColor='red');"
  >Change background to red
</a>
```

## 2.7. Operatori bit-a-bit

In JS esistono gli stessi operatori bit a bit del C++.

E' introdotto in aggiunta due nuovi operatori:

- `>>>`: Zero-fill right shift

## 2.8. Cicli

Anche i cicli sono identici a quelli del C++, con le keyword `while`, `for`, `do-while`.

Nel caso di loop infiniti il browser si blocca.
Alcuni browser invece terminano lo script.

```js
let count = 0;
while (count < 10) {
  // do something
  // ...
  count++;
}
count = 0;
do {
  // do something
  // ...
  count++;
} while (count < 10);

for (let i = 0; i < 10; i++) {
  // do something with i
  // ...
}
```

## 2.9. Gestione Eccezioni

JS implementa un sistema di gestione delle eccezioni tramite blocchi `try{}catch(){}`.

Tuttavia non sono molto utilizzati

```js
try {
  nonexistentfunction("hello");
} catch (err) {
  alert("An exception was caught:" + err);
}
```

## 2.10. Array e iteratori

Gli array sono tra le strutture dati più utilizzate.
Esistono due metodi per dichiarare un array in JS

```js
const years = [1855, 1649, 1420];

const years = new Array(1855, 1649, 1420);
```

Per iterare un array esistono due metodi:

```js
// Iterazione tramite indice
for(int i = 0; i < years.lenght; ++i){
    //...
}

// Iteratore agli elementi
for(let yr of years){
    //...
}
```

Per copiare i valori di un array:

```js
const arr = ["1", "2", "3", "4"];
let first = league[0];
let second = league[1];
let third = league[2];

// oppure

let [first, second, third] = league;
```
