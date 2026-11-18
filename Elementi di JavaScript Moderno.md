---
title: Elementi di JavaScript Moderno
---

# 1. Index

<!--toc:start-->

- [1. Index](#1-index)
- [2. Elementi di JavaScript Moderno](#2-elementi-di-javascript-moderno)
  - [2.1. `for of`](#21-for-of)
  - [2.2. Destricturing assignment](#22-destricturing-assignment)
  - [2.3. Template String Literals](#23-template-string-literals)
  - [2.4. Classi](#24-classi)
  - [2.5. Strict Mode](#25-strict-mode)
  - [2.6. Arrow Function](#26-arrow-function)
  - [2.7. Operatore Spread](#27-operatore-spread)
  <!--toc:end-->

# 2. Elementi di JavaScript Moderno

Nelle ultime versioni di JS sono stati introdotti una serie di meccanismi oggi ampiamente utilizzati e supportati che permettono di facilitare la vita del programmatore.

## 2.1. `for of`

Introdotto in _ES6_, può essere utilizzato con qualsiasi oggetto iterabile.
Quelli non iterabili generano un `TypeError` a _runtime_

```js
let mya = [11, 2, 3, 55, 4, 12, 32];

for (let x of mya) {
  console.log(x);
  /*
   * 1
   * 2
   * 3
   * 55
   * 4
   * 12
   * 32
   */
}
```

Per poter utilizzare il `for of` in un oggetto invece del `for in`. è vecessario prima utilizzare i metodi `Object.values()`, `Object.keys()` oppure `Object.entries()`:

```js
let o1 = {
  a: "one",
  b: "two",
  c: 3,
};

for (let x of Object.keys(o1)) {
  console.log(x + ": " + o1[x]);
  /*
   * a: one
   * b: two
   * c: 3
   */
}

for (let x of Object.values(o1)) {
  console.log(typeof x + " " + x);
  /*
   * string one
   * string two
   * number 3
   */
}

for (let [kk, vv] of Object.entries(o1)) {
  console.log(kk + ": " + vv);
  /*
   * a: one
   * b: two
   * c: 3
   */
}

let q = {};
for (let c of "Progettazione Web") {
  if (q[c]) q[c]++;
  else q[c] = 1;
}

console.log(q);
/*
 * {
 * P: 1,
 * r: 1,
 * o: 2,
 * g: 1,
 * e: 3,
 * t: 2,
 * a: 1,
 * z: 1,
 * i: 1,
 * n: 1,
 * ' ': 1,
 * W: 1,
 * b: 1
 * }
 */
```

## 2.2. Destricturing assignment

Introdotto in _ES6_, mermette di assegnare in maniera multipla dei valori

```js
let [a, b, c] = [10, 20, 30];
console.log(a + " " + b + " " + c);
// 10 20 30

[a, b] = [b, a];
console.log(a + " " + b);
// 20 10

[a, b] = ["ABC", "DEF", "GHI"];
console.log(a + " " + b + " " + c);
// ABC DEF 30

let [x, y, z] = [1, 2];
console.log(x + " " + y + " " + z);
// 1 2 undefined

[, x, , y, , z] = ["a", "b", "c", "d", "e", "f"];
console.log(x + " " + y + " " + z);
// b d f
```

Può essere utilizzato sia con funzioni che con oggetti:

```js
// Can be used with functions
function myfun() {
  let p = 100,
    q = 200;
  // ...
  return [p, q];
}

[x, y] = myfun();
console.log(x + " " + y);
// 100 200

[x, ...y] = [10, 20, 30, 40, 50, 60];
console.log("x=" + x + ", y=" + y);
// x=10 y=20,30,40,50,60

let o1 = { k1: 42, k2: 24 };
let { k1, mk2 } = o1;
console.log(k1 + " " + mk2);
// 42 undefined
```

## 2.3. Template String Literals

Introdotti in _ES6_, sono delle stringhe delimitate dal carattere `\`` che permette di inserire dei valori all'interno di esse.

```js
let topic = "Progettazione Web";
let s1 = `My favourite topic is ${topic}`;

console.log(s1);
// My favourite topic is Progettazione Web

let x = "X";
let y = 42;
let s2 = `Some text, ${x} and ${y * 2}`;
console.log(s2);
// Some text, X and 84
```

## 2.4. Classi

Introdotti in _ES6_, sono definiti in accordo con uno stile simile a quelli degli altri linguaggi _object-oriented_.

Nei metodi non si utilizza la _keyword_ `function` e il costruttore è definito dalla _keyword_ `constructor`.

```js
class Student {
  constructor(n, d) {
    this.name = n;
    this.degree = d;
    this.marks = [];
  }
  toString() {
    return `${this.name}, ${this.degree}`;
  }
  addMarks(m) {
    this.marks.push(m);
  }
  getAverage() {
    let s = 0;
    for (let m of this.marks) {
      s += m;
    }
    return s / this.marks.length;
  }
}
```

```js
let s1 = new Student("Mario", "Ing. Informatica");
console.log("s1=" + s1);
// s1=Mario, Ing. Informatica
let s2 = new Student("Luigi", "Computer Engineering");
console.log("s2=" + s2);
// s2=Luigi, Computer Engineering
console.log(s1.getAverage());
// NaN

s1.addMarks(27);
s1.addMarks(28);
console.log(s1.getAverage());
// 27.5
```

Nn questa versione viene implementato anche l'eredietarietà.
Per riferirsi alla _superclasse_ si utilizza la _keyword_ `super`:

```js
class WorkingStudent extends Student {
  constructor(n, d, c, f = true) {
    super(n, d);
    this.company = c;
    this.fulltime = f;
  }
  toString() {
    let s = super.toString();
    return s + `, company=${this.company}, fulltime=${this.fulltime}`;
  }
  applyBonus(b) {
    if (this.fulltime)
      for (let i = 0; i < this.marks.length; i++)
        this.marks[i] = this.marks[i] * b;
  }
}
```

```js
let w1 = new WorkingStudent("Gino", "Ing. Informatica", "Google");
w1.addMarks(30);
w1.applyBonus(1.05);
console.log("w1=" + w1);
// w1=Gino, Ing. Informatica, company=Google, fulltime=true
console.log(w1.getAverage());
// 31.5
```

## 2.5. Strict Mode

Introdotto in _ES5_, è una direttiva che è applicata inserendo l'espressione stringa `"use strict";` all'inizio di un file.

Il codice contenuto nel file avrà delle regole aggiuntive:

- Tutte le variabili **devono essere dichiarati**
- Non è possibile utilizzare `with`
- I parametri duplicati **generano errori**
- Sono effettuati cei controlli aggiuntivi

Le classi sono automaticamente in _strict mode_

```js
"use strict";

x = 21;
// x = 21;
// ^
// ReferenceError: x is not defined

let o1 = { p1: 10, p2: 20 };
with (o1) {
  console.log(p1);
  console.log(p2);
}
// with(o1) {
// ^^^^
//
// SyntaxError: Strict mode code may not include a with statement

function f(a1, a1) {
  console.log(a1);
}
f(10, 20);
// SyntaxError: Duplicate parameter name not allowed in this context
```

## 2.6. Arrow Function

Introdotte in _ES6_, è utilie quando dobbiamo utilizzare funzioni con complessità limitata.

```js
let ar1 = [10, 20, 30];

// Versione Function
ar1.forEach(function (e) {
  let t = Math.random() * e;
  console.log(t);
});
// 2.88029933302546
// 5.757679342468269
// 27.80074927780763

// Versione Arrow Function
ar1.forEach((e) => {
  let t = Math.random() * e;
  console.log(t);
});
// 9.58533802031983
// 8.773334995700527
// 12.840542468303616
```

## 2.7. Operatore Spread

Introdotto con _EC6_, l'operatore di _spread_ `...` può essere utilizzato con gli arrays

```js
let a1 = [10, 20, 30, 50];
let a2 = [1, ...a1, 100];
console.log(a2, "\n");
// [1, 10, 20, 30, 50, 100]

let v = ["first", "second", "third"];
// copia con riferimento
let c = [...v];
console.log(c, "\n");
// [ 'first', 'second', 'third' ]

let x1 = [
  { AAA: 1, BBB: 2 },
  { CCC: 3, DDD: 4 },
];
let x2 = [...x1];
x1[0].AAA = 999;
console.log(x2, "\n");
// [ { AAA: 999, BBB: 2 }, { CCC: 3, DDD: 4 } ]

let s = "This is a sentence";
let charactersOfS = [...s];
console.log(charactersOfS, "\n");
// ['T',  'h', 'i',  's', ' ', 'i',  's', ' ', 'a', ' ', 's', 'e', 'n', 't',  'e', 'n', 'c', 'e']
```

Può essere utilizzato anche con gli oggetti, anche se è poco adoperato:

```js
let stud1 = { name: "Mario", averageGrade: 25 };
let r1 = { ...stud1, course: "Programmazione Web" };
console.log(r1, "\n");
// { name: 'Mario', averageGrade: 25, course: 'Programmazione Web' }

// --- Se i nomi sono uguali, vince l'ultimo ---//
let r2 = { ...stud1, name: "Gino" };
console.log(r2, "\n");
// { name: 'Gino', averageGrade: 25 }

// --- Le proprietà ereditate non vengono considerate dallo spread --- //
let p1 = { myproperty: "ABC" };
let p2 = Object.create(p1);
console.log(p2.myproperty);
// ABC
let p3 = { ...p2 };
console.log(p3.myproperty);
// undefined
```
