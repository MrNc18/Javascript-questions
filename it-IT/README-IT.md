<div align="center">
  <img height="60" src="https://img.icons8.com/color/344/javascript.png">
  <h1>Domande di JavaScript</h1>

---

<span>Posto domande a risposta multipla sulle mie [Instagram](https://www.instagram.com/theavocoder) **stories**, che poi posterรฒ anche qui! Ultimo aggiornamento: <a href=#20220523><b>23 Maggio</b></a>

Da base ad avanzato: metti alla prova quanto conosci JavaScript, rinfresca un po' le tue conoscenze o preparati per il tuo colloquio di programmazione! :muscle: :rocket: Aggiorno regolarmente questo repository con nuove domande. Ho aggiunto le risposte nelle **sezioni compresse** sotto le domande, cliccaci sopra per espanderle. ร solo per divertimento, buona fortuna! :heart:


Sentiti libero di contattarmi! ๐ <br />
<a href="https://www.instagram.com/theavocoder">Instagram</a> || <a href="https://www.twitter.com/lydiahallie">Twitter</a> || <a href="https://www.linkedin.com/in/lydia-hallie">LinkedIn</a> || <a href="https://www.lydiahallie.dev">Blog</a>
</div>

| Sentiti libero di usarli in un progetto! ๐  Apprezzerei _molto_ un riferimento a questa repository, creo le domande e le spiegazioni (sรฌ, sono triste lol) e la community mi aiuta tantissimo a mantenerlo e migliorarlo! ๐ช๐ผ Grazie e buon divertimento!  |


Traduzione a cura di: <a href="https://github.com/luciacenetiempo">Lucia Cenetiempo</a>
|---|

---

<details><summary><b> Vedi le 18 traduzioni disponibili ๐ธ๐ฆ๐ช๐ฌ๐ง๐ฆ๐ฉ๐ช๐ช๐ธ๐ซ๐ท๐ฎ๐ฉ๐ฏ๐ต๐ฐ๐ท๐ณ๐ฑ๐ง๐ท๐ท๐บ๐น๐ญ๐น๐ท๐บ๐ฆ๐ป๐ณ๐จ๐ณ๐น๐ผ</b></summary>
<p>

- [๐ธ๐ฆ ุงูุนุฑุจูุฉ](../ar-AR/README_AR.md)
- [๐ช๐ฌ ุงููุบุฉ ุงูุนุงููุฉ](../ar-EG/README_ar-EG.md)
- [๐ง๐ฆ Bosanski](../bs-BS/README-bs_BS.md)
- [๐ฉ๐ช Deutsch](../de-DE/README.md)
- [๐ฌ๐ง English](../README.md)
- [๐ช๐ธ Espaรฑol](../es-ES/README-ES.md)
- [๐ซ๐ท Franรงais](../fr-FR/README_fr-FR.md)
- [๐ฎ๐ฉ Indonesia](../id-ID/README.md)
- [๐ฏ๐ต ๆฅๆฌ่ช](../ja-JA/README-ja_JA.md)
- [๐ฐ๐ท ํ๊ตญ์ด](../ko-KR/README-ko_KR.md)
- [๐ณ๐ฑ Nederlands](../nl-NL/README.md)
- [๐ง๐ท Portuguรชs Brasil](../pt-BR/README_pt_BR.md)
- [๐ท๐บ ะ?ัััะบะธะน](../ru-RU/README.md)
- [๐น๐ญ เนเธเธข](../th-TH/README-th_TH.md)
- [๐น๐ท Tรผrkรงe](../tr-TR/README-tr_TR.md)
- [๐บ๐ฆ ะฃะบัะฐัะฝััะบะฐ ะผะพะฒะฐ](../uk-UA/README.md)
- [๐ป๐ณ Tiแบฟng Viแปt](../vi-VI/README-vi.md)
- [๐จ๐ณ ็ฎไฝไธญๆ](../zh-CN/README-zh_CN.md)
- [๐น๐ผ ็น้ซไธญๆ](../zh-TW/README_zh-TW.md)

</p>
</details>

---

###### 1. Qual รจ l'output?

```javascript
function sayHi() {
  console.log(name);
  console.log(age);
  var name = 'Lydia';
  let age = 21;
}

sayHi();
```

- A: `Lydia` e `undefined`
- B: `Lydia` e `ReferenceError`
- C: `ReferenceError` e `21`
- D: `undefined` e `ReferenceError`

<details>
<summary><b>Risposta</b></summary>
<p>

#### Risposta: D

All'interno della funzione, dichiariamo prima la variabile `name` con la parola chiave `var`. Ciรฒ significa che la variabile viene sollevata all'interno del codice (ovvero lo spazio di memoria viene impostato durante la fase di creazione) e viene inizializzata con il valore predefinito di `undefined`, finchรฉ non arriviamo effettivamente alla riga in cui la definiamo. 
Al momento in cui proviamo ad eseguire il log della variabile `name` non l'abbiamo ancora dichiarata, quindi mantiene il valore di `undefined`. 

Le variabili dichiarate con la chiave `let` (o `const`) vengono sollevate, ma a differenza delle variabili dichiarate con `var`, non vengono <i>inizializzate</i>. Per questo motivo non sono accessibili prima della loro dichiarazione (dove le inizializzaimo). Questa รจ chiamata "temporal dead zone". Quando proviamo ad accedere alle variabili prima che vengano dichiarate, JavaScript genera un `ReferenceError`.

</p>
</details>

---

###### 2. Qual รจ l'output?

```javascript
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 1);
}

for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 1);
}
```

- A: `0 1 2` e `0 1 2`
- B: `0 1 2` e `3 3 3`
- C: `3 3 3` e `0 1 2`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

A causa della coda degli eventi in JavaScript la funzione di callback `setTimeout` viene chiamata _dopo_ che il loop รจ stato eseguito. Poichรฉ la variabile `i` nel primo loop รจ stata dichiarata usando la chiave `var`, questo valore รจ globale. Durante il loop abbiamo incrementato ogni volta il valore di `i` di `1` usando l'operatore unario `++`. Quando รจ stata invocata la funzione di callback `setTimeout`, `i` nel primo esempio risultava sin dal principio uguale a `3`.

Nel secondo loop, la variabile `i` รจ stata dichiarata usando la chiave `let`: le variabili dichiarate con la chiave `let` (e `const`) hanno lo scope del blocco (un blocco รจ qualsiasi cosa tra `{ }`). Durante ogni iterazione, `i` avrร? un nuovo valore e ogni valore avrร? lo scope all'interno del loop.

</p>
</details>

---

###### 3. Qual รจ l'output?

```javascript
const shape = {
  radius: 10,
  diameter() {
    return this.radius * 2;
  },
  perimeter: () => 2 * Math.PI * this.radius,
};

console.log(shape.diameter());
console.log(shape.perimeter());
```

- A: `20` e `62.83185307179586`
- B: `20` e `NaN`
- C: `20` e `63`
- D: `NaN` e `63`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Il valore di `diameter` รจ una funzione regolare, mentre il valore di `perimeter` รจ generato con una arrow function.

Nelle arrow functions, la chiave `this` fa riferimento al suo scope interno a differenza delle funzioni regolari. Questo vuol dire che quando richiamiamo `perimeter` non stiamo facendo riferimento all'oggetto shape, ma al suo ambito circostante (ad esempio window).

Non troviamo quindi alcun valore `radius` in quell'oggetto e quindi viene restituito `NaN`.

</p>
</details>

---

###### 4. Qual รจ l'output?

```javascript
+true;
!'Lydia';
```

- A: `1` and `false`
- B: `false` and `NaN`
- C: `false` and `false`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Il + unario tenta di convertire un operando in un numero. `true` equivale ad `1` e `false` equivale a `0`.

La stringa `'Lydia'` รจ un valore veritiero. Quello che in realtร? ci stiamo chiedendo con `!'Lydia'` รจ "questo valore veritiero รจ falso?". Per cui la risposta รจ `false`.

</p>
</details>

---

###### 5. Quale affermazione รจ vera?

```javascript
const bird = {
  size: 'small',
};

const mouse = {
  name: 'Mickey',
  small: true,
};
```

- A: `mouse.bird.size` non รจ valido
- B: `mouse[bird.size]` non รจ valido
- C: `mouse[bird["size"]]` non รจ valido
- D: Sono tutte valide

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

In JavaScript, tutte le chiavi degli oggetti sono stringhe (a meno che non sia un simbolo). Anche se potremmo non scriverle come stringhe, vengono sempre convertite come tali.

JavaScript interpreta le istruzioni, quindi quando usiamo la bracket notation, vede la prima parentesi aperta `[` e continua finchรฉ non trova la parentesi chiusa `]`. Solo allora valuterร? la dichiarazione.

Quando in JavaScript richiamiamo `mouse[bird.size]`: per prima cosa viene valorizzato `bird.size`, che รจ `"small"`, per JS viene tradotto quindi come `mouse["small"]` che restituisce `true`.

Con l'utilizzo del punto questo non accade perchรฉ `mouse` non ha una chiave chiamata `bird`, e questo significa che `mouse.bird` รจ `undefined`. Per JavaScript quindi l'istruzione `mouse.bird.size` viene tradotta con `mouse.undefined.size` che รจ un valore non valido e che quindi genererร? un errore simile a `Cannot read property "size" of undefined`.

</p>
</details>

---

###### 6. Qual รจ l'output?

```javascript
let c = { greeting: 'Hey!' };
let d;

d = c;
c.greeting = 'Hello';
console.log(d.greeting);
```

- A: `Hello`
- B: `Hey!`
- C: `undefined`
- D: `ReferenceError`
- E: `TypeError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

In JavaScript, tutti gli oggetti interagiscono per _referenza_.

La variabile `c` contiene come valore un oggetto. Alla variabile `d` assegniamo come valore il riferimento di `c` che quindi contiene l'oggetto (e non un suo clone).

<img src="https://i.imgur.com/ko5k0fs.png" width="200">

Quando modifichi il valore di questo oggetto, lo stai modificando sia per `c`che per `d`, che contiene il suo riferimento.

</p>
</details>

---

###### 7. Qual รจ l'output?

```javascript
let a = 3;
let b = new Number(3);
let c = 3;

console.log(a == b);
console.log(a === b);
console.log(b === c);
```

- A: `true` `false` `true`
- B: `false` `false` `true`
- C: `true` `false` `false`
- D: `false` `true` `true`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

`new Number()` รจ una funzione costruttore integrata. Nonostante sembri un numero, in realtร? non lo รจ, si tratta infatti di un oggetto con un sacco di funzioni extra.

Quando utilizziamo l'operatore `==`, stiamo verificando solo se il suo _valore_ รจ uguale. Entrambe le variabili hanno il valore di `3`, quindi il primo log restituisce `true`.

Quando invece utilizziamo l'operatore `===`, stiamo verificando che sia il valore che il tipo di valore siano uguali. `new Number()` non รจ un numero, รจ un **oggetto** quindi entrambi i log restituiscono `false`.

</p>
</details>

---

###### 8. Qual รจ l'output?

```javascript
class Chameleon {
  static colorChange(newColor) {
    this.newColor = newColor;
    return this.newColor;
  }

  constructor({ newColor = 'green' } = {}) {
    this.newColor = newColor;
  }
}

const freddie = new Chameleon({ newColor: 'purple' });
console.log(freddie.colorChange('orange'));
```

- A: `orange`
- B: `purple`
- C: `green`
- D: `TypeError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

La funzione `colorChange` รจ statica. I metodi statici sono progettati per vivere solo nel costruttore in cui vengono creati e non possono essere passati a nessun figlio o richiamati su istanze di classe. Poichรฉ `freddie` รจ un'istanza della classe `Chameleon`, la funzione non puรฒ essere chiamata su di essa. Viene restituito quindi un errore di tipo `TypeError`.

</p>
</details>

---

###### 9. Qual รจ l'output?

```javascript
let greeting;
greetign = {}; // Typo!
console.log(greetign);
```

- A: `{}`
- B: `ReferenceError: greetign is not defined`
- C: `undefined`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Il nostro log restituisce un oggetto perchรฉ abbiamo appena creato un oggetto vuoto come oggetto globale nel momento in cui per errore abbiamo digitato `greetign` al posto di `greeting`.

Il nostro interprete a quel punto ha letto `global.greetign = {}` (o `window.greetign = {}` se parliamo di un browser).

Per evitare ciรฒ, possiamo usare `"use strict"`. Questo assicura di aver dichiarato una variabile prima di impostarla uguale a qualsiasi cosa.

</p>
</details>

---

###### 10. Cosa succede se facciamo questo?

```javascript
function bark() {
  console.log('Woof!');
}

bark.animal = 'dog';
```

- A: Niente, va benissimo!
- B: `SyntaxError`. Non รจ possibile aggiungere proprietร? a una funzione in questo modo.
- C: `"Woof"` viene registrato.
- D: `ReferenceError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

In JavaScript non succede nulla, perchรฉ le funzioni sono oggetti! (Tutto tranne i tipi primitivi sono oggetti).

Una funzione รจ un tipo speciale di oggetto. Il codice che scrivi non รจ la funzione effettiva. La funzione รจ un oggetto con delle proprietร? e quindi questa proprietร? รจ invocabile.

</p>
</details>

---

###### 11. Qual รจ l'output?

```javascript
function Person(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}

const member = new Person('Lydia', 'Hallie');
Person.getFullName = function() {
  return `${this.firstName} ${this.lastName}`;
};

console.log(member.getFullName());
```

- A: `TypeError`
- B: `SyntaxError`
- C: `Lydia Hallie`
- D: `undefined` `undefined`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

In JavaScript, le funzioni sono oggetti e quindi il metodo `getFullName` viene aggiunto al costruttore della funzione stessa. Per questo motivo possiamo chiamare `Person.getFullName()`, mentre `member.getFullName` genera un `TypeError`.

Se vuoi che un metodo sia disponibile per tutte le istanze dell'oggetto, devi aggiungerlo alla proprietร? del prototipo:


```js
Person.prototype.getFullName = function() {
  return `${this.firstName} ${this.lastName}`;
};
```

</p>
</details>

---

###### 12. Qual รจ l'output?

```javascript
function Person(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}

const lydia = new Person('Lydia', 'Hallie');
const sarah = Person('Sarah', 'Smith');

console.log(lydia);
console.log(sarah);
```

- A: `Person {firstName: "Lydia", lastName: "Hallie"}` and `undefined`
- B: `Person {firstName: "Lydia", lastName: "Hallie"}` and `Person {firstName: "Sarah", lastName: "Smith"}`
- C: `Person {firstName: "Lydia", lastName: "Hallie"}` and `{}`
- D: `Person {firstName: "Lydia", lastName: "Hallie"}` and `ReferenceError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Per la const `sarah`, non abbiamo usato la chiave `new`. Quando si usa `new`, `this` si riferisce al nuovo oggetto vuoto che creiamo. Tuttavia, se non aggiungiamo `new`, `this` si riferisce all'**oggetto globale**!

Abbiamo quindi scritto che `this.firstName` equivale a `"Sarah"` e `this.lastName` equivale a `"Smith"`. Quello che abbiamo effettivamente fatto รจ definire `global.firstName = 'Sarah'` e `global.lastName = 'Smith'`. La `const` `sarah` viene lasciata come `non definita`, perchรฉ non restituiamo un valore dalla funzione `Persona`.

</p>
</details>

---

###### 13. Quali sono le tre fasi della propagazione degli eventi?

- A: Target > Capturing > Bubbling
- B: Bubbling > Target > Capturing
- C: Target > Bubbling > Capturing
- D: Capturing > Target > Bubbling

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

Durante la fase di **capturing**, l'evento passa attraverso gli elementi predecessori fino all'elemento target. Quindi raggiunge l'elemento **target** e inizia il **bubbling**.

<img src="https://i.imgur.com/N18oRgd.png" width="200">

</p>
</details>

---

###### 14. Tutti gli oggetti hanno prototipi.

- A: true
- B: false

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Tutti gli oggetti hanno prototipi, ad eccezione dell'**oggetto base**. L'oggetto base รจ l'oggetto creato dall'utente, o un oggetto creato usando la parola chiave `new`. L'oggetto base ha accesso ad alcuni metodi e proprietร?, come `.toString`. Questo รจ il motivo per cui puoi utilizzare i metodi JavaScript built-in! Tutti questi metodi sono disponibili sul prototype. Quindi, anche se JavaScript non riesce a trovarlo direttamente sul tuo oggetto, scende lungo la chain del prototype e lo trova lรฌ, il che lo rende accessibile anche per l'oggetto creato da te.

</p>
</details>

---

###### 15. Qual รจ l'output?

```javascript
function sum(a, b) {
  return a + b;
}

sum(1, '2');
```

- A: `NaN`
- B: `TypeError`
- C: `"12"`
- D: `3`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

JavaScript รจ un **linguaggio tipizzato dinamicamente**: non specifichiamo quali tipi siano determinate variabili. I valori possono essere automaticamente convertiti in un altro tipo, questa azione รจ chiamata _coercizione implicita del tipo_. **Coercizione** รจ la conversione da un tipo all'altro.

In questo esempio, JavaScript converte il numero `1` in una stringa, in modo che la funzione abbia un senso e restituisca un valore. Durante l'aggiunta di un tipo numerico (`1`) e di un tipo stringa (`'2'`), il numero viene trattato come una stringa. Possiamo concatenare stringhe come `"Hello" + "World"`, quindi quello che sta succedendo qui รจ `"1" + "2"` che restituisce `"12"`.

</p>
</details>

---

###### 16. Qual รจ l'output?

```javascript
let number = 0;
console.log(number++);
console.log(++number);
console.log(number);
```

- A: `1` `1` `2`
- B: `1` `2` `2`
- C: `0` `2` `2`
- D: `0` `1` `2`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Utilizzando l'operatore unario come **postfisso** `number++` succede che:

1. Restituisce prima il suo valore (`0`)
2. Subito dopo incrementa il valore di 1 (quindi รจ ora `1`)

Utilizzando l'operatore unario come **prefisso** `++number` succede che:

1. Incrementa prima il valore (il numero รจ ora `2`)
2. Restituisce subito dopo il valore giร? incrementato (`2`)

Quindi il nostro log sarร?  `0 2 2`.

</p>
</details>

---

###### 17. Qual รจ l'output?

```javascript
function getPersonInfo(one, two, three) {
  console.log(one);
  console.log(two);
  console.log(three);
}

const person = 'Lydia';
const age = 21;

getPersonInfo`${person} is ${age} years old`;
```

- A: `"Lydia"` `21` `["", " is ", " years old"]`
- B: `["", " is ", " years old"]` `"Lydia"` `21`
- C: `"Lydia"` `["", " is ", " years old"]` `21`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Utilizzando i template literals, il valore del primo argomento sarร? un array di valori della stringa. Gli altri argomenti prenderanno i valori dell'espressione passata. 

</p>
</details>

---

###### 18. Qual รจ l'output?

```javascript
function checkAge(data) {
  if (data === { age: 18 }) {
    console.log('You are an adult!');
  } else if (data == { age: 18 }) {
    console.log('You are still an adult.');
  } else {
    console.log(`Hmm.. You don't have an age I guess`);
  }
}

checkAge({ age: 18 });
```

- A: `You are an adult!`
- B: `You are still an adult.`
- C: `Hmm.. You don't have an age I guess`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Quando si verifica l'uguaglianza, i primitivi vengono confrontati in base al loro _valore_, mentre gli oggetti vengono confrontati in base al loro _riferimento_. JavaScript controlla se gli oggetti hanno un riferimento alla stessa posizione in memoria.

I due oggetti che stiamo confrontando non lo hanno: l'oggetto che abbiamo passato come parametro si riferisce a una posizione di memoria diversa rispetto all'oggetto che abbiamo usato per verificare l'uguaglianza.

Questo รจ il motivo per cui sia `{ age: 18 } === { age: 18 }` e `{ age: 18 } == { age: 18 }` restituiscono `false`.

</p>
</details>

---

###### 19. Qual รจ l'output?

```javascript
function getAge(...args) {
  console.log(typeof args);
}

getAge(21);
```

- A: `"number"`
- B: `"array"`
- C: `"object"`
- D: `"NaN"`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Il parametro rest (`...args`) ci permette di "collettare" tutti gli argomenti in un array. L'array รจ un oggetto, quindi `typeof args` restituisce `"oggetto"`

</p>
</details>

---

###### 20. Qual รจ l'output?

```javascript
function getAge() {
  'use strict';
  age = 21;
  console.log(age);
}

getAge();
```

- A: `21`
- B: `undefined`
- C: `ReferenceError`
- D: `TypeError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Con `"use strict"`, puoi assicurarti di non dichiarare variabili globali per sbaglio. In questo caso la variabile `age` non รจ mai stata dichiarata, e siccome usiamo `"use strict"`, genererร? un `ReferenceError`. Se non avessimo usato `"use strict"`, avrebbe funzionato perchรฉ la proprietร? `age` sarebbe stata aggiunta all'oggetto globale.

</p>
</details>

---

###### 21. Qual รจ il valore di `sum`?

```javascript
const sum = eval('10*10+5');
```

- A: `105`
- B: `"105"`
- C: `TypeError`
- D: `"10*10+5"`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

`eval` "valuta" i codici passati come stringa. Se รจ un'espressione, come in questo caso, valuta l'espressione. L'espressione รจ `10 * 10 + 5`. Quindi il valore restituito รจ il numero `105`.

</p>
</details>

---

###### 22. Per quanto tempo cool_secret รจ accessibile?

```javascript
sessionStorage.setItem('cool_secret', 123);
```

- A: Per sempre, i dati non vanno persi.
- B: Fin quando l'utente chiude la scheda.
- C: Fin quando l'utente chiude l'intero browser, non solo la scheda.
- D: Fin quando l'utente spegne il proprio computer.

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

I dati memorizzati in `sessionStorage` vengono rimossi dopo aver chiuso la _tab_.

Se avessi usato `localStorage`, i dati sarebbero rimasti lรฌ per sempre, a meno che, ad esempio, non fosse stato invocato `localStorage.clear()`.

</p>
</details>

---

###### 23. Qual รจ l'output?

```javascript
var num = 8;
var num = 10;

console.log(num);
```

- A: `8`
- B: `10`
- C: `SyntaxError`
- D: `ReferenceError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Con la chiave `var` puoi dichiarare piรน variabili con lo stesso nome. La variabile conterrร? quindi l'ultimo valore.

Non puoi farlo con `let` o `const` poichรฉ sono block-scoped.

</p>
</details>

---

###### 24. Qual รจ l'output?

```javascript
const obj = { 1: 'a', 2: 'b', 3: 'c' };
const set = new Set([1, 2, 3, 4, 5]);

obj.hasOwnProperty('1');
obj.hasOwnProperty(1);
set.has('1');
set.has(1);
```

- A: `false` `true` `false` `true`
- B: `false` `true` `true` `true`
- C: `true` `true` `false` `true`
- D: `true` `true` `true` `true`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Tutte le chiavi degli oggetti (esclusi i simboli) sono stringhe, anche se non vengono scritte come tali. Questo รจ il motivo per cui anche `obj.hasOwnProperty('1')` restituisce true.

Per i set non funziona allo stesso modo degli oggetti. Non c'รจ alcun `'1'` nel nostro set, per cui `set.has('1')` restituisce `false`, รจ perรฒ presente il tipo numerico `1` per cui `set.has(1)` restituisce `true`.

</p>
</details>

---

###### 25. Qual รจ l'output?

```javascript
const obj = { a: 'one', b: 'two', a: 'three' };
console.log(obj);
```

- A: `{ a: "one", b: "two" }`
- B: `{ b: "two", a: "three" }`
- C: `{ a: "three", b: "two" }`
- D: `SyntaxError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Se hai due chiavi con lo stesso nome, questa verrร? sostituita. Sarร? quindi ancora nella sua prima posizione, ma con l'ultimo valore specificato.

</p>
</details>

---

###### 26. Il contesto di esecuzione globale JavaScript crea due cose: l'oggetto globale e la parola chiave "this".

- A: true
- B: false
- C: it depends

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Il contesto di esecuzione di base รจ il contesto di esecuzione globale: รจ ciรฒ che รจ accessibile ovunque nel codice.

</p>
</details>

---

###### 27. Qual รจ l'output?

```javascript
for (let i = 1; i < 5; i++) {
  if (i === 3) continue;
  console.log(i);
}
```

- A: `1` `2`
- B: `1` `2` `3`
- C: `1` `2` `4`
- D: `1` `3` `4`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

L'istruzione `continue` salta un'iterazione se una certa condizione restituisce `true`.

</p>
</details>

---

###### 28. Qual รจ l'output?

```javascript
String.prototype.giveLydiaPizza = () => {
  return 'Just give Lydia pizza already!';
};

const name = 'Lydia';

console.log(name.giveLydiaPizza())
```

- A: `"Just give Lydia pizza already!"`
- B: `TypeError: not a function`
- C: `SyntaxError`
- D: `undefined`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

`String` รจ un costruttore built-in, a cui possiamo aggiungere proprietร?. In questo caso รจ stato appena aggiunto un metodo al suo prototipo. 
Le stringhe primitive vengono automaticamente convertite in un oggetto stringa, generato dalla string prototype function. Quindi, tutte le stringhe hanno accesso a quel metodo!

</p>
</details>

---

###### 29. Qual รจ l'output?

```javascript
const a = {};
const b = { key: 'b' };
const c = { key: 'c' };

a[b] = 123;
a[c] = 456;

console.log(a[b]);
```

- A: `123`
- B: `456`
- C: `undefined`
- D: `ReferenceError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Le chiavi degli oggetti vengono automaticamente convertite in stringhe. Stiamo cercando di impostare un oggetto come chiave per l'oggetto `a` con il valore di `123`.

Tuttavia, quando convertiamo in stringa un oggetto, diventa `"[object Object]"`. Quindi quello che stiamo dicendo qui รจ che `a["[object Object]"] = 123`. `c` รจ un altro oggetto che stiamo implicitamente stringendo. Quindi, `a["[object Object]"] = 456`.

Quindi, quando facciamo console.log di `a[b]`, che in realtร? รจ `a["[object Object]"]` che abbiamo appena valorizzato con `456`, restituisce `456`.

</p>
</details>

---

###### 30. Qual รจ l'output?

```javascript
const foo = () => console.log('First');
const bar = () => setTimeout(() => console.log('Second'));
const baz = () => console.log('Third');

bar();
foo();
baz();
```

- A: `First` `Second` `Third`
- B: `First` `Third` `Second`
- C: `Second` `First` `Third`
- D: `Second` `Third` `First`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Abbiamo una funzione `setTimeout` e l'abbiamo invocata per prima. Eppure, viene loggata per ultima.

Questo succede perchรฉ nei browser non abbiamo solo il runtime engine, ma anche qualcosa chiamata `WebAPI`. La `WebAPI` ci fornisce la funzione `setTimeout` con cui iniziare, e per esempio il DOM.

Dopo che la _callback_ รจ stata inviata alla `WebAPI`, la stessa funzione `setTimeout` (ma non la sua callback) viene eliminata dallo stack.

<img src="https://i.imgur.com/X5wsHOg.png" width="200">

Ora, `foo` viene invocato e `"First"` viene loggato.

<img src="https://i.imgur.com/Pvc0dGq.png" width="200">

`foo` viene quindi tolto dallo stack e `baz` viene invocato. `"Third"` viene loggato.

<img src="https://i.imgur.com/WhA2bCP.png" width="200">

La WebAPI non puรฒ semplicemente aggiungere elementi allo stack ogni volta che รจ pronta, spinge quindi la funzione di callback in quella che chiamiamo _queue_.

<img src="https://i.imgur.com/NSnDZmU.png" width="200">

ร qui che un ciclo di eventi inizia a funzionare. Un **event loop** esamina lo stack e la coda delle attivitร?. Se lo stack รจ vuoto, prende la prima cosa in coda e la inserisce nello stack.

<img src="https://i.imgur.com/uyiScAI.png" width="200">

`bar` viene invocato, `"Second"` viene registrato e viene tolto dallo stack.

</p>
</details>

---

###### 31. Quale sarร? event.target cliccando sul bottone?

```html
<div onclick="console.log('first div')">
  <div onclick="console.log('second div')">
    <button onclick="console.log('button')">
      Click!
    </button>
  </div>
</div>
```

- A: `div` esterno
- B: `div` interno
- C: `button`
- D: Un array di tutti gli elementi nidificati

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

L'elemento annidato piรน in profonditร? รจ quello che ha causato l'evento ed รจ quindi l'event.target. Puoi stoppare la propagazione con `event.stopPropagation`

</p>
</details>

---

###### 32. Cliccando sul paragrafo, quale sarร? l'output loggato?

```html
<div onclick="console.log('div')">
  <p onclick="console.log('p')">
    Click here!
  </p>
</div>
```

- A: `p` `div`
- B: `div` `p`
- C: `p`
- D: `div`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Se clicchiamo su `p`, vediamo due log: `p` e `div`. Durante la propagazione dell'evento, ci sono 3 fasi: capturing, target, e bubbling. Di default, i gestori di eventi vengono eseguiti nella fase di bubbling (a meno che non si imposti `useCapture` su `true`) e va quindi dall'elemento annidato piรน profondo verso l'esterno.

</p>
</details>

---

###### 33. Qual รจ l'output?

```javascript
const person = { name: 'Lydia' };

function sayHi(age) {
  return `${this.name} is ${age}`;
}

console.log(sayHi.call(person, 21));
console.log(sayHi.bind(person, 21));
```

- A: `undefined is 21` `Lydia is 21`
- B: `function` `function`
- C: `Lydia is 21` `Lydia is 21`
- D: `Lydia is 21` `function`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

Con entrambi possiamo passare l'oggetto a cui vogliamo che la chiave `this` faccia riferimento. Tuttavia, anche `.call` viene _eseguito immediatamente_!

`.bind.` restituisce una _copia_ della funzione, ma con un contesto vincolato! Non viene eseguito immediatamente.

</p>
</details>

---

###### 34. Qual รจ l'output?

```javascript
function sayHi() {
  return (() => 0)();
}

console.log(typeof sayHi());
```

- A: `"object"`
- B: `"number"`
- C: `"function"`
- D: `"undefined"`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

La funzione `sayHi` restituisce il valore dato dell'espressione della immediately invoked function expression (IIFE). Questa funzione ha restituito `0`, che รจ di tipo `"numero"`.

Ci sono solo 7 tipi built-in: `null`, `undefined`, `boolean`, `number`, `string`, `object` e `symbol`. `"function"` non รจ un tipo, poichรฉ le funzioni sono oggetti, รจ quindi di tipo "oggetto"`.

</p>
</details>

---

###### 35. Quale di questi valori รจ falso?

```javascript
0;
new Number(0);
('');
(' ');
new Boolean(false);
undefined;
```

- A: `0`, `''`, `undefined`
- B: `0`, `new Number(0)`, `''`, `new Boolean(false)`, `undefined`
- C: `0`, `''`, `new Boolean(false)`, `undefined`
- D: Sono tutti falsi

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Ci sono 8 valori falsi:

- `undefined`
- `null`
- `NaN`
- `false`
- `''` (empty string)
- `0`
- `-0`
- `0n` (BigInt(0))

I costruttori di funzioni, come `new Number` e `new Boolean` sono veritieri.

</p>
</details>

---

###### 36. Qual รจ l'output?

```javascript
console.log(typeof typeof 1);
```

- A: `"number"`
- B: `"string"`
- C: `"object"`
- D: `"undefined"`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

`typeof 1` ritorna `"number"`.
`typeof "number"` ritorna `"string"`

</p>
</details>

---

###### 37. Qual รจ l'output?

```javascript
const numbers = [1, 2, 3];
numbers[10] = 11;
console.log(numbers);
```

- A: `[1, 2, 3, 7 x null, 11]`
- B: `[1, 2, 3, 11]`
- C: `[1, 2, 3, 7 x empty, 11]`
- D: `SyntaxError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Quando imposti un valore su un elemento in un array che supera la lunghezza dell'array JavaScript crea degli "slot vuoti". Questi in realtร? hanno il valore di `undefined`, ma vedrai qualcosa come:

`[1, 2, 3, 7 x empty, 11]`

a seconda di dove lo esegui (รจ diverso per ogni browser, node, ecc.)

</p>
</details>

---

###### 38. Qual รจ l'output?

```javascript
(() => {
  let x, y;
  try {
    throw new Error();
  } catch (x) {
    (x = 1), (y = 2);
    console.log(x);
  }
  console.log(x);
  console.log(y);
})();
```

- A: `1` `undefined` `2`
- B: `undefined` `undefined` `undefined`
- C: `1` `1` `2`
- D: `1` `undefined` `undefined`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Il blocco `catch` riceve l'argomento `x` ma non รจ la stessa `x` della variabile, bensรฌ passiamo un argomento della funzione. Questa "variabile" `x` รจ block-scoped quindi ha un ambito di blocco.

Subito dopo impostiamo il valore di variabile block-scoped a `1` e impostiamo il valore della variabile `y`. Ora facciamo un console.log della variabile block-scoped `x`, che รจ uguale a `1`.

Fuori dal blocco `catch`, `x` รจ ancora `undefined` e `y` รจ `2` quindi quando facciamo `console.log(x)` al di fuori del blocco `catch`, otterremo `undefined` e `y` restituirร? `2`.

</p>
</details>

---

###### 39. Tutto in JavaScript รจ...

- A: o un primitivo o un oggetto
- B: o una funzione o un oggetto
- C: Questa รจ una domanda trabocchetto! Sono solo oggetti
- D: un numero o un oggetto

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

JavaScript ha solo tipi primitivi e oggetti.

I tipi primitivi sono `boolean`, `null`, `undefined`, `bigint`, `number`, `string` e `symbol`.

Ciรฒ che differenzia un tipo primitivo da un oggetto รจ che i primitivi non hanno proprietร? o metodi. Tuttavia, noterai che `'foo'.toUpperCase()` restituisce `'FOO'` e non genera un `TypeError`. Questo perchรฉ quando si tenta di accedere a una proprietร? o a un metodo su di un tipo primitivo come lo รจ una stringa, JavaScript racchiuderร? implicitamente il tipo primitivo utilizzando una delle classi wrapper, ovvero "String", valuterร? l'espressione ed eliminerร? il wrapper una volta terminato. Tutti i primitivi tranne `null` e `undefined` subiscono questo comportamento.

</p>
</details>

---

###### 40. Qual รจ l'output?

```javascript
[[0, 1], [2, 3]].reduce(
  (acc, cur) => {
    return acc.concat(cur);
  },
  [1, 2],
);
```

- A: `[0, 1, 2, 3, 1, 2]`
- B: `[6, 1, 2]`
- C: `[1, 2, 0, 1, 2, 3]`
- D: `[1, 2, 6]`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

`[1, 2]` rappresenta il nostro valore interno. Ovvero il valore con cui iniziamo e il valore del primo `acc`. Durante il primo round, `acc` รจ `[1,2]` e `cur` รจ `[0, 1]`. Li concateniamo ottenendo `[1, 2, 0, 1]`.

A questo punto `acc` corrisponderร? a `[1, 2, 0, 1]` e `cur` sarร? ancora `[2, 3]`. Li concateniamo e otteniamo `[1, 2, 0, 1, 2, 3]`
</p>
</details>

---

###### 41. Qual รจ l'output?

```javascript
!!null;
!!'';
!!1;
```

- A: `false` `true` `false`
- B: `false` `false` `true`
- C: `false` `true` `true`
- D: `true` `true` `false`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

`null` รจ falso. `!null` restituisce `true`. `!true` restituisce `false`.

`""` รจ falso. `!""` restituisce `true`. `!true` restituisce `false`.

`1` รจ vero. `!1` restituisce `falso`. `!false` restituisce `true`.

</p>
</details>

---

###### 42. Cosa restituisce il metodo `setInterval` nel browser?

```javascript
setInterval(() => console.log('Hi'), 1000);
```

- A: un ID univoco
- B: la quantitร? di millisecondi specificata
- C: la funzione passata
- D: `undefined`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Restituisce un ID univoco. Questo id puรฒ essere usato per cancellare quell'intervallo con la funzione `clearInterval()`.

</p>
</details>

---

###### 43. Cosa restituisce?

```javascript
[...'Lydia'];
```

- A: `["L", "y", "d", "i", "a"]`
- B: `["Lydia"]`
- C: `[[], "Lydia"]`
- D: `[["L", "y", "d", "i", "a"]]`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Una stringa รจ un iterabile. L'operatore spread mappa ogni carattere di una stringa rendendola parte di array.

</p>
</details>

---

###### 44. Qual รจ l'output?

```javascript
function* generator(i) {
  yield i;
  yield i * 2;
}

const gen = generator(10);

console.log(gen.next().value);
console.log(gen.next().value);
```

- A: `[0, 10], [10, 20]`
- B: `20, 20`
- C: `10, 20`
- D: `0, 10 and 10, 20`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Le funzioni regolari non possono essere interrotte a metร? dopo l'invocazione. Tuttavia, una funzione "generator" puรฒ essere stoppata a metร? e in seguito continuare da dove si era interrotta. Ogni volta che una funzione generator incontra una parola chiave `yield`, la funzione restituisce il valore specificato dopo di essa. Nota che la funzione del generator in quel caso non _restituisce (return)_ il valore, _rende (yeld)_ il valore.

Come prima cosa inizializziamo la funzione del generator con `i` uguale a `10`. Invochiamo la funzione usando il metodo `next()`. La prima volta che invochiamo la funzione generator, `i` รจ uguale a `10`, incontra la prima parola chiave `yield` quindi restituisce il valore di `i`. Il generatore รจ ora "in pausa" e `10` viene loggato.

Invochiamo di nuovo la funzione con il metodo `next()`. Inizia a continuare da dove si era fermata in precedenza, sempre con `i` uguale a `10`. Ora incontra il secondo `yield` e restituisce `i * 2`, quindi restituisce `10 * 2`, che รจ `20`. Ciรฒ risulta in `10, 20`.

</p>
</details>

---

###### 45. Cosa restituisce?

```javascript
const firstPromise = new Promise((res, rej) => {
  setTimeout(res, 500, 'one');
});

const secondPromise = new Promise((res, rej) => {
  setTimeout(res, 100, 'two');
});

Promise.race([firstPromise, secondPromise]).then(res => console.log(res));
```

- A: `"one"`
- B: `"two"`
- C: `"two" "one"`
- D: `"one" "two"`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Quando passiamo piรน promises al metodo `Promise.race`, questo risolve/rifiuta la _prima_ promise. Al metodo `setTimeout` passiamo un timer: 500ms per la prima promise (`firstPromise`) e 100ms per la seconda promise (`secondPromise`). Ciรฒ significa che `secondPromise` si risolve prima con il valore di `'due'`. `res` ora contiene il valore di `'two'`, che viene loggato.

</p>
</details>

---

###### 46. Qual รจ l'output?

```javascript
let person = { name: 'Lydia' };
const members = [person];
person = null;

console.log(members);
```

- A: `null`
- B: `[null]`
- C: `[{}]`
- D: `[{ name: "Lydia" }]`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

Per prima cosa, dichiariamo una variabile `person` con un oggetto che ha una proprietร? `name`.

<img src="https://i.imgur.com/TML1MbS.png" width="200">

Quindi, dichiariamo una variabile chiamata `members`. Impostiamo il primo elemento di quell'array uguale al valore della variabile `person`. Gli oggetti interagiscono per _riferimento_ quando vengono impostati uguali tra loro. Quando assegni un riferimento da una variabile all'altra, esegui una _copia_ di quel riferimento. (nota che non hanno lo _stesso_ riferimento!)

<img src="https://i.imgur.com/FSG5K3F.png" width="300">

Quindi, impostiamo la variabile `person` uguale a `null`.

<img src="https://i.imgur.com/sYjcsMT.png" width="300">

Stiamo modificando solo il valore della variabile `person`, e non il primo elemento nell'array, poichรฉ quell'elemento ha un riferimento diverso (copiato) dall'oggetto. Il primo elemento in `members` mantiene ancora il suo riferimento all'oggetto originale. Quando logghiamo l'array `members`, il primo elemento contiene ancora il valore dell'oggetto, che viene loggato.

</p>
</details>

---

###### 47. Qual รจ l'output?

```javascript
const person = {
  name: 'Lydia',
  age: 21,
};

for (const item in person) {
  console.log(item);
}
```

- A: `{ name: "Lydia" }, { age: 21 }`
- B: `"name", "age"`
- C: `"Lydia", 21`
- D: `["name", "Lydia"], ["age", 21]`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Con il ciclo `for-in`, possiamo iterare le chiavi degli oggetti, in questo caso `name` e `age`. Le chiavi degli oggetti sono stringhe (se non sono un simbolo). In ogni ciclo, impostiamo il valore di `item` uguale alla chiave corrente su cui sta iterando. Il primo `item` รจ uguale a `name` e viene loggato, `item` sarร? poi uguale a `age`, che viene loggato.

</p>
</details>

---

###### 48. Qual รจ l'output?

```javascript
console.log(3 + 4 + '5');
```

- A: `"345"`
- B: `"75"`
- C: `12`
- D: `"12"`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

L'associazione รจ l'ordine in cui il compilatore valuta le espressioni, da sinistra a destra o da destra a sinistra. Questo accade solo se tutti gli operatori hanno la _stessa_ precedenza. Abbiamo solo un tipo di operatore: `+`. Inoltre, l'associazione รจ da sinistra a destra.

`3 + 4` viene valutato per primo. E risulta nell'addizione dei due valori che restituiscono quindi `7`.

`7 + '5'` risulta in `"75"` per via della coercizione. JavaScript converte il numero `7` in una stringa, (vedi la domanda 15). Possiamo concatenare due stringhe usando l'operatore `+`. `"7" + "5"` risulta quindi in "75"`.

</p>
</details>

---

###### 49. Qual รจ il valore di `num`?

```javascript
const num = parseInt('7*6', 10);
```

- A: `42`
- B: `"42"`
- C: `7`
- D: `NaN`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Viene restituito solo il primo valore della stringa. In base alla _radice_ (ovvero il secondo argomento per specificare sulla base di quale tipo di numero vogliamo analizzarlo: base 10, esadecimale, ottale, binario, ecc.), `parseInt` controlla se i caratteri nella stringa sono validi. Una volta che incontra un carattere che non รจ un numero valido nella radice, interrompe l'analisi e ignora i seguenti caratteri.

`*` non รจ un numero valido. Analizza solo `"7"` nel decimale `7`. `num` ora contiene il valore di `7`.

</p>
</details>

---

###### 50. Qual รจ l'output?

```javascript
[1, 2, 3].map(num => {
  if (typeof num === 'number') return;
  return num * 2;
});
```

- A: `[]`
- B: `[null, null, null]`
- C: `[undefined, undefined, undefined]`
- D: `[ 3 x empty ]`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Quando si esegue il mapping sull'array, il valore di `num` รจ uguale all'elemento su cui sta attualmente scorrendo. In questo caso, gli elementi sono numeri, quindi la condizione dell'istruzione if `typeof num === "number"` restituisce `true`. La funzione map crea un nuovo array e inserisce i valori restituiti dalla funzione.

Tuttavia, non ritorniamo un valore. Quando non ritorniamo un valore dalla funzione, la funzione restituisce `undefined`. Per ogni elemento nell'array, viene chiamato il blocco funzione, quindi per ogni elemento restituiamo `undefined`.

</p>
</details>

---

###### 51. Qual รจ l'output?

```javascript
function getInfo(member, year) {
  member.name = 'Lydia';
  year = '1998';
}

const person = { name: 'Sarah' };
const birthYear = '1997';

getInfo(person, birthYear);

console.log(person, birthYear);
```

- A: `{ name: "Lydia" }, "1997"`
- B: `{ name: "Sarah" }, "1998"`
- C: `{ name: "Lydia" }, "1998"`
- D: `{ name: "Sarah" }, "1997"`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Gli argomenti vengono passati come _valori_, a meno che il loro valore non sia un oggetto, quindi vengono passati come _reference_. `birthYear` viene passato per valore, poichรฉ รจ una stringa, non un oggetto. Quando passiamo argomenti per valore, viene creata una _copia_ di quel valore (vedi domanda 46).

La variabile `birthYear` ha un riferimento al valore `"1997"`. Anche l'argomento `year` fa riferimento al valore `"1997"`, ma non รจ lo stesso valore a cui fa riferimento `birthYear`. Quando aggiorniamo il valore di `year` impostando `year` uguale a `"1998"`, stiamo solo aggiornando il valore di `year`. `birthYear` รจ ancora uguale a `"1997"`.

Il valore di `person` รจ un oggetto. L'argomento `member` ha un riferimento (copiato) dello stesso oggetto. Quando modifichiamo una proprietร? dell'oggetto a cui `member` fa riferimento, verrร? modificato anche il valore di `person`, poichรฉ entrambi hanno un riferimento allo stesso oggetto. La proprietร? `name` di `person` รจ ora uguale al valore `"Lydia"`
</p>
</details>

---

###### 52. Qual รจ l'output?

```javascript
function greeting() {
  throw 'Hello world!';
}

function sayHi() {
  try {
    const data = greeting();
    console.log('It worked!', data);
  } catch (e) {
    console.log('Oh no an error:', e);
  }
}

sayHi();
```

- A: `It worked! Hello world!`
- B: `Oh no an error: undefined`
- C: `SyntaxError: can only throw Error objects`
- D: `Oh no an error: Hello world!`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

Con l'istruzione `throw`, possiamo creare errori personalizzati. Con questa istruzione, puoi generare eccezioni. Un'eccezione puรฒ essere una <b>stringa</b>, un <b>numero</b>, un <b>booleano</b> o un <b>oggetto</b>. In questo caso, la nostra eccezione รจ la stringa `'Hello world!'`.

Con l'istruzione `catch`, possiamo specificare cosa fare se viene generata un'eccezione nel blocco `try`. Viene generata un'eccezione: la stringa `'Hello world!'`. `e` รจ ora uguale a quella stringa, che logghiamo. Ciรฒ si traduce in `'Oh an error: Hello world!'`.

</p>
</details>

---

###### 53. Qual รจ l'output?

```javascript
function Car() {
  this.make = 'Lamborghini';
  return { make: 'Maserati' };
}

const myCar = new Car();
console.log(myCar.make);
```

- A: `"Lamborghini"`
- B: `"Maserati"`
- C: `ReferenceError`
- D: `TypeError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Quando si restituisce una proprietร?, il valore della proprietร? รจ uguale al valore _restituito_, non al valore impostato nella funzione di costruzione. Restituiamo la stringa `"Maserati"`, quindi `myCar.make` รจ uguale a `"Maserati"`.

</p>
</details>

---

###### 54. Qual รจ l'output?

```javascript
(() => {
  let x = (y = 10);
})();

console.log(typeof x);
console.log(typeof y);
```

- A: `"undefined", "number"`
- B: `"number", "number"`
- C: `"object", "number"`
- D: `"number", "undefined"`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

`let x = (y = 10);` in realtร? รจ un'abbreviazione per:

```javascript
y = 10;
let x = y;
```

Quando impostiamo `y` uguale a `10`, in realtร? aggiungiamo una proprietร? `y` all'oggetto globale (`window` nel browser, `global` in Node). In un browser, `window.y` ora รจ uguale a `10`.

Quindi, dichiariamo una variabile `x` con il valore di `y`, che รจ `10`. Le variabili dichiarate con la parola chiave `let` sono _block scoped_, ovvero sono definite solo all'interno del blocco in cui sono dichiarate, l'espressione di funzione immediatamente invocata (IIFE) in questo caso. Quando utilizziamo l'operatore `typeof`, l'operando `x` non รจ definito: stiamo cercando di accedere a `x` al di fuori del blocco in cui รจ dichiarato. Ciรฒ significa che `x` non รจ definito. I valori a cui non รจ stato assegnato un valore o dichiarati sono di tipo `"undefined"`. `console.log(typeof x)` restituisce `"undefined"`.

Tuttavia, abbiamo creato una variabile globale `y` quando abbiamo impostato `y` uguale a `10`. Questo valore รจ accessibile ovunque nel nostro codice. `y` รจ definito e contiene un valore di tipo `"number"`. `console.log(typeof y)` restituisce `"number"`.

</p>
</details>

---

###### 55. Qual รจ l'output?

```javascript
class Dog {
  constructor(name) {
    this.name = name;
  }
}

Dog.prototype.bark = function() {
  console.log(`Woof I am ${this.name}`);
};

const pet = new Dog('Mara');

pet.bark();

delete Dog.prototype.bark;

pet.bark();
```

- A: `"Woof I am Mara"`, `TypeError`
- B: `"Woof I am Mara"`, `"Woof I am Mara"`
- C: `"Woof I am Mara"`, `undefined`
- D: `TypeError`, `TypeError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Possiamo eliminare le proprietร? dagli oggetti usando la parola chiave `delete`, anche sul prototype. Eliminando una proprietร? sul prototipo, questa non รจ piรน disponibile nella catena di prototype. In questo caso, la funzione `bark` non รจ piรน disponibile sul prototipo dopo `delete Dog.prototype.bark`, ma proviamo comunque ad accedervi.

Quando proviamo a invocare qualcosa che non รจ una funzione, viene lanciato un `TypeError`. In questo caso `TypeError: pet.bark is not a function`, poichรฉ `pet.bark` รจ `undefined`.

</p>
</details>

---

###### 56. Qual รจ l'output?

```javascript
const set = new Set([1, 1, 2, 3, 4]);

console.log(set);
```

- A: `[1, 1, 2, 3, 4]`
- B: `[1, 2, 3, 4]`
- C: `{1, 1, 2, 3, 4}`
- D: `{1, 2, 3, 4}`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

L'oggetto `Set` รจ una collezione di valori _unici_: un valore puรฒ verificarsi solo una volta in un set.

Abbiamo passato l'array `[1, 1, 2, 3, 4]` con il valore duplicato `1`. Poichรฉ non possiamo avere due valori uguali in un set, uno di essi viene rimosso. Ciรฒ risulta in `{1, 2, 3, 4}`.

</p>
</details>

---

###### 57. Qual รจ l'output?

```javascript
// counter.js
let counter = 10;
export default counter;
```

```javascript
// index.js
import myCounter from './counter';

myCounter += 1;

console.log(myCounter);
```

- A: `10`
- B: `11`
- C: `Error`
- D: `NaN`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Un modulo importato รจ di _sola lettura_: non รจ quindi possibile modificare il modulo importato. Solo il modulo che li esporta puรฒ cambiarne il valore.

Quando proviamo ad incrementare il valore di `myCounter`, viene generato un errore: perchรฉ `myCounter` รจ di sola lettura e non puรฒ essere modificato.

</p>
</details>

---

###### 58. Qual รจ l'output?

```javascript
const name = 'Lydia';
age = 21;

console.log(delete name);
console.log(delete age);
```

- A: `false`, `true`
- B: `"Lydia"`, `21`
- C: `true`, `true`
- D: `undefined`, `undefined`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

L'operatore `delete` restituisce un valore booleano: `true` su una cancellazione riuscita, altrimenti restituirร? `false`. Tuttavia, le variabili dichiarate con la parola chiave `var`, `const` o `let` non possono essere cancellate usando l'operatore `delete`.

La variabile `name` รจ stata dichiarata con la chiave `const`, quindi la sua cancellazione non va a buon fine e viene restituito `false`. Quando impostiamo `age` uguale a `21`, abbiamo effettivamente aggiunto una proprietร? chiamata `age` all'oggetto globale. Puoi eliminare con successo le proprietร? dagli oggetti in questo modo, anche l'oggetto globale, quindi `delete age` restituisce `true`.

</p>
</details>

---

###### 59. Qual รจ l'output?

```javascript
const numbers = [1, 2, 3, 4, 5];
const [y] = numbers;

console.log(y);
```

- A: `[[1, 2, 3, 4, 5]]`
- B: `[1, 2, 3, 4, 5]`
- C: `1`
- D: `[1]`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Possiamo spacchettare i valori da un array o proprietร? dagli oggetti attraverso la destrutturazione. Per esempio:

```javascript
[a, b] = [1, 2];
```

<img src="https://i.imgur.com/ADFpVop.png" width="200">

Il valore di `a` ora รจ `1`, e il valore di `b` รจ ora `2`. Quello che abbiamo effettivamente fatto nella domanda รจ:

```javascript
[y] = [1, 2, 3, 4, 5];
```

<img src="https://i.imgur.com/NzGkMNk.png" width="200">

Questo significa che il valore di `y` รจ uguale al primo valore nell'array, che รจ il numero `1`. Quando registriamo `y`, viene restituito `1`.

</p>
</details>

---

###### 60. Qual รจ l'output?

```javascript
const user = { name: 'Lydia', age: 21 };
const admin = { admin: true, ...user };

console.log(admin);
```

- A: `{ admin: true, user: { name: "Lydia", age: 21 } }`
- B: `{ admin: true, name: "Lydia", age: 21 }`
- C: `{ admin: true, user: ["Lydia", 21] }`
- D: `{ admin: true }`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

ร possibile combinare oggetti utilizzando l'operatore spread `...`. Questo ti consente di creare copie delle coppie chiave/valore di un oggetto e aggiungerle a un altro oggetto. In questo caso, creiamo copie dell'oggetto `user` e le aggiungiamo all'oggetto `admin`. L'oggetto `admin` ora contiene le coppie chiave/valore copiate, che risultano in `{ admin: true, name: "Lydia", age: 21 }`.

</p>
</details>

---

###### 61. Qual รจ l'output?

```javascript
const person = { name: 'Lydia' };

Object.defineProperty(person, 'age', { value: 21 });

console.log(person);
console.log(Object.keys(person));
```

- A: `{ name: "Lydia", age: 21 }`, `["name", "age"]`
- B: `{ name: "Lydia", age: 21 }`, `["name"]`
- C: `{ name: "Lydia"}`, `["name", "age"]`
- D: `{ name: "Lydia"}`, `["age"]`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Con il metodo `defineProperty`, possiamo aggiungere nuove proprietร? a un oggetto o modificare quelle esistenti. Quando aggiungiamo delle proprietร? a un oggetto usando il metodo `defineProperty`, queste per impostazione predefinita sono _non enumerabili_. Il metodo `Object.keys` restituisce tutti i nomi di proprietร? _enumerabili_ da un oggetto, in questo caso solo `"name"`.

Le proprietร? aggiunte usando il metodo `defineProperty` sono immutabili per impostazione predefinita. Puoi ignorare questo comportamento usando le proprietร? `writable`, `configurable` ed `enumerable`. In questo modo, il metodo `defineProperty` ti dร? molto piรน controllo sulle proprietร? che stai aggiungendo a un oggetto.

</p>
</details>

---

###### 62. Qual รจ l'output?

```javascript
const settings = {
  username: 'lydiahallie',
  level: 19,
  health: 90,
};

const data = JSON.stringify(settings, ['level', 'health']);
console.log(data);
```

- A: `"{"level":19, "health":90}"`
- B: `"{"username": "lydiahallie"}"`
- C: `"["level", "health"]"`
- D: `"{"username": "lydiahallie", "level":19, "health":90}"`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Il secondo argomento di `JSON.stringify` รจ _replacer_. Il replacer puรฒ essere una funzione o un array e consente di controllare cosa e come i valori devono essere stringati.

Se il replacer รจ un _array_, solo i nomi delle proprietร? inclusi nell'array verranno aggiunti alla stringa JSON. In questo caso, sono incluse solo le proprietร? con i nomi `"level"` e `"health"`, `"username"` รจ esclusa. `data` quindi ora รจ uguale a `"{"level":19, "health":90}"`.

Se il replacer รจ una _funzione_, questa funzione viene chiamata su ogni proprietร? nell'oggetto che stai stringendo. Il valore restituito da questa funzione sarร? il valore della proprietร? quando viene aggiunto alla stringa JSON. Se il valore รจ `undefined`, questa proprietร? viene esclusa dalla stringa JSON.

</p>
</details>

---

###### 63. Qual รจ l'output?

```javascript
let num = 10;

const increaseNumber = () => num++;
const increasePassedNumber = number => number++;

const num1 = increaseNumber();
const num2 = increasePassedNumber(num1);

console.log(num1);
console.log(num2);
```

- A: `10`, `10`
- B: `10`, `11`
- C: `11`, `11`
- D: `11`, `12`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

L'operatore unario `++` _prima_ restituisce il valore dell'operando, _poi_ incrementa il valore dell'operando. Il valore di `num1` รจ `10`, poichรฉ la funzione `increaseNumber` restituisce prima il valore di `num`, che รจ `10`, e solo successivamente incrementa il valore di `num`.

`num2` รจ `10`, poichรฉ abbiamo passato `num1` a `increasePassedNumber`. `number` รจ uguale a `10` (il valore di `num1`. Anche in questo caso, l'operatore unario `++` _prima_ restituisce il valore dell'operando, _poi_ lo incrementa. Il valore di `number` รจ ` 10`, quindi `num2` รจ uguale a `10`.

</p>
</details>

---

###### 64. Qual รจ l'output?

```javascript
const value = { number: 10 };

const multiply = (x = { ...value }) => {
  console.log((x.number *= 2));
};

multiply();
multiply();
multiply(value);
multiply(value);
```

- A: `20`, `40`, `80`, `160`
- B: `20`, `40`, `20`, `40`
- C: `20`, `20`, `20`, `40`
- D: `NaN`, `NaN`, `20`, `40`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

In ES6, possiamo inizializzare i parametri con un valore predefinito. Il valore del parametro sarร? il valore predefinito se nessun altro valore รจ stato passato alla funzione o se รจ stato passato un valore `"undefined"`. In questo caso, distribuiamo le proprietร? dell'oggetto `value` in un nuovo oggetto, quindi `x` ha il valore predefinito di `{ number: 10 }`.

L'argomento predefinito viene valutato quando viene chiamato! Ogni volta che chiamiamo la funzione, viene creato un _nuovo_ oggetto. Invochiamo la funzione `multiply` le prime due volte senza passare un valore, quindi `x` ha il valore predefinito di `{ number: 10 }`. Quindi logghiamo il valore moltiplicato di quel numero, che รจ `20`.

La terza volta che invochiamo la funzione multiply, passiamo un argomento: l'oggetto chiamato `value`. L'operatore `*=` รจ in realtร? un'abbreviazione per `x.number = x.number * 2`: modifichiamo il valore di `x.number` e logghiamo il valore moltiplicato `20`.

La quarta volta, passiamo di nuovo l'oggetto `value`, in questo caso `x.number` รจ stato precedentemente modificato in `20`, quindi `x.number *= 2` logga `40`.

</p>
</details>

---

###### 65. Qual รจ l'output?

```javascript
[1, 2, 3, 4].reduce((x, y) => console.log(x, y));
```

- A: `1` `2` and `3` `3` and `6` `4`
- B: `1` `2` and `2` `3` and `3` `4`
- C: `1` `undefined` and `2` `undefined` and `3` `undefined` and `4` `undefined`
- D: `1` `2` and `undefined` `3` and `undefined` `4`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

Il primo argomento che il metodo `reduce` riceve รจ l'_accumulatore_, in questo caso `x`. Il secondo argomento รจ il _valore corrente_ `y`. 
Con il metodo reduce, eseguiamo una funzione di callback su ogni elemento dell'array, che alla fine potrebbe risultare in un singolo valore.

In questo esempio, non stiamo restituendo alcun valore, stiamo semplicemente loggando i valori dell'accumulatore e il valore corrente.

Il valore dell'accumulatore รจ uguale al valore restituito in precedenza dalla funzione di callback. Se non si passa l'argomento opzionale `initialValue` al metodo `reduce`, l'accumulatore รจ uguale al primo elemento della prima chiamata.

Alla prima chiamata, l'accumulatore (`x`) รจ `1` e il valore corrente (`y`) รจ `2`. Non facciamo un return con la funzione di callback ma logghiamo l'accumulatore e il valore corrente: `1` e `2` vengono loggati.

Se non restituisci un valore da una funzione questa restituisce `undefined`. Alla chiamata successiva, l'accumulatore รจ `undefined` e il valore corrente รจ "3". `undefined` e `3` vengono loggati.

Alla quarta chiamata, di nuovo non facciamo un return dalla funzione di callback. L'accumulatore รจ di nuovo `undefined` e il valore corrente รจ "4". `undefined` e `4` vengono loggati.
</p>
</details>
  
---

###### 66. Con quale costruttore possiamo estendere la classe `Dog`?

```javascript
class Dog {
  constructor(name) {
    this.name = name;
  }
};

class Labrador extends Dog {
  // 1
  constructor(name, size) {
    this.size = size;
  }
  // 2
  constructor(name, size) {
    super(name);
    this.size = size;
  }
  // 3
  constructor(size) {
    super(name);
    this.size = size;
  }
  // 4
  constructor(name, size) {
    this.name = name;
    this.size = size;
  }

};
```

- A: 1
- B: 2
- C: 3
- D: 4

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

In una classe derivata, non puoi accedere alla chiave `this` prima di chiamare `super`. Se provi a farlo, genererร? un ReferenceError: 1 e 4 genererebbero un errore di riferimento.

Con la chiave `super`, chiamiamo il costruttore di quella classe parent con gli argomenti forniti. Il costruttore del parent riceve l'argomento `name`, quindi passiamo `name` a `super`.

La classe `Labrador` riceve due argomenti, `name` poichรฉ estende `Dog`, e `size` come proprietร? extra sulla classe `Labrador`. Entrambi devono essere passati alla funzione di costruzione su `Labrador`, cosa che viene eseguita correttamente usando il costruttore 2.

</p>
</details>

---

###### 67. Qual รจ l'output?

```javascript
// index.js
console.log('running index.js');
import { sum } from './sum.js';
console.log(sum(1, 2));

// sum.js
console.log('running sum.js');
export const sum = (a, b) => a + b;
```

- A: `running index.js`, `running sum.js`, `3`
- B: `running sum.js`, `running index.js`, `3`
- C: `running sum.js`, `3`, `running index.js`
- D: `running index.js`, `undefined`, `running sum.js`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Con la chiave `import` tutti i moduli importati sono _pre-parsed_. Ciรฒ significa che i moduli importati vengono eseguiti _prima_, il codice nel file che importa il modulo viene eseguito _dopo_.

Questa รจ una delle differenze tra `require()` in CommonJS e `import`. Con `require()`, puoi caricare le dipendenze su richiesta mentre il codice รจ in esecuzione. Se avessimo usato `require` invece di `import`, sulla console avremmo loggato `running index.js`, `running sum.js`, `3`.

</p>
</details>

---

###### 68. Qual รจ l'output?

```javascript
console.log(Number(2) === Number(2));
console.log(Boolean(false) === Boolean(false));
console.log(Symbol('foo') === Symbol('foo'));
```

- A: `true`, `true`, `false`
- B: `false`, `true`, `false`
- C: `true`, `false`, `true`
- D: `true`, `true`, `true`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Ogni Simbolo รจ unico. Lo scopo dell'argomento passato a Symbol รจ di dargli una descrizione. Il valore del Symbol non dipende dall'argomento passato. Mentre testiamo l'uguaglianza, stiamo creando due simboli completamente nuovi: il primo `Symbol('foo')` e il secondo `Symbol('foo')`. Questi due valori sono unici e non uguali tra loro, `Symbol('foo') === Symbol('foo')` quindi restituisce `false`.

</p>
</details>

---

###### 69. Qual รจ l'output?

```javascript
const name = 'Lydia Hallie';
console.log(name.padStart(13));
console.log(name.padStart(2));
```

- A: `"Lydia Hallie"`, `"Lydia Hallie"`
- B: `" Lydia Hallie"`, `" Lydia Hallie"` (`"[13x whitespace]Lydia Hallie"`, `"[2x whitespace]Lydia Hallie"`)
- C: `" Lydia Hallie"`, `"Lydia Hallie"` (`"[1x whitespace]Lydia Hallie"`, `"Lydia Hallie"`)
- D: `"Lydia Hallie"`, `"Lyd"`,

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Con il metodo `padStart`, possiamo aggiungere un riempimento all'inizio di una stringa. Il valore passato a questo metodo รจ la lunghezza _totale_ della stringa insieme al riempimento. La stringa `"Lydia Hallie"` ha una lunghezza di `12`. `name.padStart(13)` inserisce quindi 1 spazio all'inizio della stringa, perchรฉ 12 + 1 รจ 13.

Se l'argomento passato al metodo `padStart` รจ inferiore alla lunghezza dell'array, non verrร? aggiunto alcun riempimento.

</p>
</details>

---

###### 70. Qual รจ l'output?

```javascript
console.log('๐ฅ' + '๐ป');
```

- A: `"๐ฅ๐ป"`
- B: `257548`
- C: Una stringa contenente i code points
- D: Errore

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Con l'operatore `+` puoi concatenare stringhe. In questo caso, stiamo concatenando la stringa `"๐ฅ"` con la stringa `"๐ป"`, ottenendo `"๐ฅ๐ป"`.

</p>
</details>

---

###### 71. Come possiamo loggare i valori commentati dopo l'istruzione console.log?

```javascript
function* startGame() {
  const answer = yield 'Do you love JavaScript?';
  if (answer !== 'Yes') {
    return "Oh wow... Guess we're gone here";
  }
  return 'JavaScript loves you back โค๏ธ';
}

const game = startGame();
console.log(/* 1 */); // Do you love JavaScript?
console.log(/* 2 */); // JavaScript loves you back โค๏ธ
```

- A: `game.next("Yes").value` and `game.next().value`
- B: `game.next.value("Yes")` and `game.next.value()`
- C: `game.next().value` and `game.next("Yes").value`
- D: `game.next.value()` and `game.next.value("Yes")`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Una funzione generator "mette in pausa" la sua esecuzione quando incontra la parola chiave `yield`. Innanzitutto dobbiamo lasciare che la funzione produca la stringa "Ami JavaScript?", che puรฒ essere eseguita chiamando `game.next().value`.

Ogni riga viene quindi eseguita, finchรฉ non trova la prima chiave `yield`. C'รจ una parola chiave `yield` sulla prima riga all'interno della funzione: l'esecuzione si interrompe con il primo rendimento! _Questo significa che la variabile `answer` non รจ ancora definita!_

Quando chiamiamo `game.next("Yes").value`, il precedente `yield` viene sostituito con il valore dei parametri passati alla funzione `next()`, in questo caso `"Yes"`. Il valore della variabile `answer` รจ ora uguale a `"Yes"`. La condizione dell'istruzione if restituisce `false` e `JavaScript loves you back โค๏ธ` viene registrato.

</p>
</details>

---

###### 72. Qual รจ l'output?

```javascript
console.log(String.raw`Hello\nworld`);
```

- A: `Hello world!`
- B: `Hello` <br />&nbsp; &nbsp; &nbsp;`world`
- C: `Hello\nworld`
- D: `Hello\n` <br /> &nbsp; &nbsp; &nbsp;`world`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

`String.raw` restituisce una stringa in cui gli escape (`\n`, `\v`, `\t` ecc.) vengono ignorati! I backslash possono essere un problema poichรฉ potresti finire con qualcosa del tipo:

`` const path = `C:\Documents\Projects\table.html` ``

Il che risulterebbe in:

`"C:DocumentsProjects able.html"`

Con `String.raw`, il compilatore ignorerebbe semplicemente l'escape e stamperebbe:

`C:\Documents\Projects\table.html`

In questo caso, รจ la stringa `Hello\nworld` che viene loggata.

</p>
</details>

---

###### 73. Qual รจ l'output?

```javascript
async function getData() {
  return await Promise.resolve('I made it!');
}

const data = getData();
console.log(data);
```

- A: `"I made it!"`
- B: `Promise {<resolved>: "I made it!"}`
- C: `Promise {<pending>}`
- D: `undefined`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Una funzione asincrona restituisce sempre una promise. L'`await` deve ancora attendere che la promise si risolva: una promise in sospeso viene restituita quando chiamiamo `getData()` per impostare `data` uguale ad essa.

Se volessimo accedere al valore risolto `"I made it"`, potremmo usare il metodo `.then()` su `data`:

`data.then(res => console.log(res))`

Questo avrebbe loggato `"I made it!"`

</p>
</details>

---

###### 74. Qual รจ l'output?

```javascript
function addToList(item, list) {
  return list.push(item);
}

const result = addToList('apple', ['banana']);
console.log(result);
```

- A: `['apple', 'banana']`
- B: `2`
- C: `true`
- D: `undefined`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Il metodo `.push()` restituisce la _lunghezza_ del nuovo array! 
Inizialmente, l'array conteneva un solo elemento (la stringa `"banana"`) e aveva una lunghezza di `1`. Dopo aver aggiunto la stringa `"apple"` allo stesso array, questo contiene due elementi e ha una lunghezza di `2` 

Attraverso la funzione `addToList`, il metodo `push` modifica l'array originale. 
Per restituire l'_array_ dalla funzione invece della _lunghezza dell'array_, serve fare un return di `list` dopo aver inserito l'`item`.

</p>
</details>

---

###### 75. Qual รจ l'output?

```javascript
const box = { x: 10, y: 20 };

Object.freeze(box);

const shape = box;
shape.x = 100;

console.log(shape);
```

- A: `{ x: 100, y: 20 }`
- B: `{ x: 10, y: 20 }`
- C: `{ x: 100 }`
- D: `ReferenceError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

`Object.freeze` rende impossibile aggiungere, rimuovere o modificare le proprietร? di un oggetto (a meno che il valore della proprietร? non sia un altro oggetto).

Quando creiamo la variabile `shape` e la impostiamo come all'oggetto congelato `box`, anche `shape` si riferisce ad un oggetto congelato. 
Puoi controllare se un oggetto รจ congelato usando `Object.isFrozen`. In questo caso, `Object.isFrozen(shape)` restituisce true, poichรฉ la variabile `shape` ha un riferimento a un oggetto congelato.

Poichรฉ `shape` รจ congelata, e poichรฉ il valore di `x` non รจ un oggetto, non possiamo modificare la proprietร? `x`. 
`x` รจ ancora uguale a `10` e `{ x: 10, y: 20 }` viene loggato.

</p>
</details>

---

###### 76. Qual รจ l'output?

```javascript
const { name: myName } = { name: 'Lydia' };

console.log(name);
```

- A: `"Lydia"`
- B: `"myName"`
- C: `undefined`
- D: `ReferenceError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Quando spacchettiamo la proprietร? `name` dall'oggetto, assegniamo il suo valore `"Lydia"` a una variabile con il nome `myName`.

Con `{ name: myName }`, diciamo a JavaScript che vogliamo creare una nuova variabile chiamata `myName` con il valore della proprietร? `name`.

Poichรฉ proviamo a loggare `name`, una variabile che non รจ definita, viene restituito `undefined` nell'assegnazione. Successivamente, il valore di `Lydia` viene memorizzato tramite l'assegnazione di destrutturazione.

</p>
</details>

---

###### 77. Questa รจ una funzione pura?

```javascript
function sum(a, b) {
  return a + b;
}
```

- A: Yes
- B: No

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Una funzione pura รจ una funzione che restituisce _sempre_ lo stesso risultato, se vengono passati gli stessi argomenti.

La funzione `sum` restituisce sempre lo stesso risultato. Se le passiamo `1` e `2`, restituirร? _sempre_ `3` senza effetti collaterali. Se passiamo `5` e `10`, restituirร? _sempre_ `15` e cosรฌ via. Questa รจ la definizione di funzione pura.

</p>
</details>

---

###### 78. Qual รจ l'output?

```javascript
const add = () => {
  const cache = {};
  return num => {
    if (num in cache) {
      return `From cache! ${cache[num]}`;
    } else {
      const result = num + 10;
      cache[num] = result;
      return `Calculated! ${result}`;
    }
  };
};

const addFunction = add();
console.log(addFunction(10));
console.log(addFunction(10));
console.log(addFunction(5 * 2));
```

- A: `Calculated! 20` `Calculated! 20` `Calculated! 20`
- B: `Calculated! 20` `From cache! 20` `Calculated! 20`
- C: `Calculated! 20` `From cache! 20` `From cache! 20`
- D: `Calculated! 20` `From cache! 20` `Error`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

La funzione `add` รจ una funzione _memoizzata_. Con la memorizzazione, possiamo memorizzare nella cache i risultati di una funzione per velocizzarne l'esecuzione. 
In questo caso, creiamo un oggetto `cache` che memorizza i valori precedentemente restituiti.

Se chiamiamo di nuovo la funzione `addFunction` con lo stesso argomento, prima controlla se ha giร? ottenuto quel valore nella sua cache, in tal caso, verrร? restituito il valore della cache, consentendo di risparmiare tempo di esecuzione. Altrimenti, se non รจ memorizzato nella cache, calcolerร? il valore e lo memorizzerร? in seguito.

Chiamiamo la funzione `addFunction` tre volte con lo stesso valore: alla prima chiamata, il valore della funzione quando `num` รจ uguale a `10` non รจ ancora memorizzato nella cache. 
La condizione dell'istruzione if `num in cache` restituisce `false`, e il blocco else viene eseguito: `Calculated! 20` viene loggato e il valore del risultato viene aggiunto all'oggetto cache. 
`cache` ora รจ uguale a `{ 10: 20 }`.

La seconda volta, l'oggetto `cache` contiene il valore che viene restituito per `10`. La condizione dell'istruzione if `num in cache` restituisce `true` e `'From cache! 20'` viene loggato.

La terza volta, passiamo `5 * 2` alla funzione che viene valutata a `10`. L'oggetto `cache` contiene il valore che viene restituito `10`. La condizione dell'istruzione if `num in cache` restituisce `true` e `'From cache! 20'` viene registrato.

</p>
</details>

---

###### 79. Qual รจ l'output?

```javascript
const myLifeSummedUp = ['โ', '๐ป', '๐ท', '๐ซ'];

for (let item in myLifeSummedUp) {
  console.log(item);
}

for (let item of myLifeSummedUp) {
  console.log(item);
}
```

- A: `0` `1` `2` `3` and `"โ"` `"๐ป"` `"๐ท"` `"๐ซ"`
- B: `"โ"` `"๐ป"` `"๐ท"` `"๐ซ"` and `"โ"` `"๐ป"` `"๐ท"` `"๐ซ"`
- C: `"โ"` `"๐ป"` `"๐ท"` `"๐ซ"` and `0` `1` `2` `3`
- D: `0` `1` `2` `3` and `{0: "โ", 1: "๐ป", 2: "๐ท", 3: "๐ซ"}`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Con un ciclo _for-in_, possiamo scorrere su proprietร? **enumerabili**. In un array, le proprietร? enumerabili sono le "chiavi" degli elementi dell'array, che sono in realtร? i loro indici. Potresti immaginare un array come:

`{0: "โ", 1: "๐ป", 2: "๐ท", 3: "๐ซ"}`

Dove le chiavi sono le proprietร? enumerabili. `0` `1` `2` `3` viene quindi loggato.

Con un ciclo _for-of_, possiamo iterare su **iterabili**. Un array รจ un iterabile. Quando iteriamo sull'array, la variabile "item" รจ uguale all'elemento su cui sta attualmente iterando, `"โ"` `"๐ป"` `"๐ท"` `"๐ซ"` viene loggato.

</p>
</details>

---

###### 80. Qual รจ l'output?

```javascript
const list = [1 + 2, 1 * 2, 1 / 2];
console.log(list);
```

- A: `["1 + 2", "1 * 2", "1 / 2"]`
- B: `["12", 2, 0.5]`
- C: `[3, 2, 0.5]`
- D: `[1, 1, 1]`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Gli elementi di un array possono contenere qualsiasi valore. Numeri, stringhe, oggetti, altri array, null, booleani, undefined e altre espressioni come date, funzioni e calcoli.

L'elemento sarร? uguale al valore restituito. `1 + 2` restituirร? quindi `3`, `1 * 2` restituirร? `2` e `1 / 2` restituirร? `0.5`.

</p>
</details>

---

###### 81. Qual รจ l'output?

```javascript
function sayHi(name) {
  return `Hi there, ${name}`;
}

console.log(sayHi());
```

- A: `Hi there,`
- B: `Hi there, undefined`
- C: `Hi there, null`
- D: `ReferenceError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Di default, gli argomenti hanno il valore di `undefined`, a meno che un valore non sia stato passato alla funzione. In questo caso, non abbiamo passato un valore per l'argomento `name`. `name` รจ uguale a `undefined` che viene loggato.

In ES6, possiamo sovrascrivere questo valore predefinito `undefined` con dei parametri predefiniti. Per esempio:

`function sayHi(name = "Lydia") { ... }`

In questo caso, se non abbiamo passato un valore o se abbiamo passato `undefined`, `name` sarร? sempre uguale alla stringa `Lydia`

</p>
</details>

---

###### 82. Qual รจ l'output?

```javascript
var status = '๐';

setTimeout(() => {
  const status = '๐';

  const data = {
    status: '๐ฅ',
    getStatus() {
      return this.status;
    },
  };

  console.log(data.getStatus());
  console.log(data.getStatus.call(this));
}, 0);
```

- A: `"๐ฅ"` e `"๐"`
- B: `"๐ฅ"` e `"๐"`
- C: `"๐"` e `"๐"`
- D: `"๐"` e `"๐"`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Il valore della parola chiave `this` dipende da dove la usi. In un **metodo**, come il metodo `getStatus`, la parola chiave `this` si riferisce all'_oggetto a cui appartiene il metodo_. Nel nostro caso il metodo appartiene all'oggetto `data`, quindi `this` si riferisce all'oggetto `data`. Quando logghiamo `this.status`, stiamo chiedendo la proprietร? `status` sull'oggetto `data` che รจ `"๐ฅ"`.

Con il metodo `call` possiamo cambiare l'oggetto a cui fa riferimento la parola chiave `this`. Nelle **funzioni**, la parola chiave `this` si riferisce all'_oggetto a cui appartiene la funzione_. Abbiamo dichiarato la funzione `setTimeout` sull'_oggetto globale_, quindi all'interno della funzione `setTimeout`, la parola chiave `this` si riferisce all'_oggetto globale_. Sull'oggetto globale c'รจ una variabile chiamata _status_ con il valore di `"๐"`. Quando si fa un console.log di `this.status`, otteniamo `"๐"`.

</p>
</details>

---

###### 83. Qual รจ l'output?

```javascript
const person = {
  name: 'Lydia',
  age: 21,
};

let city = person.city;
city = 'Amsterdam';

console.log(person);
```

- A: `{ name: "Lydia", age: 21 }`
- B: `{ name: "Lydia", age: 21, city: "Amsterdam" }`
- C: `{ name: "Lydia", age: 21, city: undefined }`
- D: `"Amsterdam"`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Impostiamo la variabile `city` uguale al valore della proprietร? chiamata `city` sull'oggetto `person`. Non c'รจ alcuna proprietร? su questo oggetto chiamato `city`, quindi la variabile `city` ha il valore di `undefined`.

Nota che _non_ stiamo facendo riferimento all'oggetto `person`! Impostiamo semplicemente la variabile `city` uguale al valore corrente della proprietร? `city` sull'oggetto `person`.

Quindi, impostiamo `city` uguale alla stringa `"Amsterdam"`. Questo non cambia l'oggetto `person`: non c'รจ alcun riferimento a quell'oggetto.

Quando si logga l'oggetto `person`, viene restituito l'oggetto non modificato.

</p>
</details>

---

###### 84. Qual รจ l'output?

```javascript
function checkAge(age) {
  if (age < 18) {
    const message = "Sorry, you're too young.";
  } else {
    const message = "Yay! You're old enough!";
  }

  return message;
}

console.log(checkAge(21));
```

- A: `"Sorry, you're too young."`
- B: `"Yay! You're old enough!"`
- C: `ReferenceError`
- D: `undefined`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Le variabili con la chiave `const` e `let` sono _block-scoped_. Un blocco รจ qualsiasi cosa si trovi tra parentesi graffe (`{ }`). In questo caso, le parentesi graffe delle istruzioni if/else. Non puoi fare riferimento a una variabile al di fuori del blocco in cui รจ dichiarata, viene quindi generato un ReferenceError.

</p>
</details>

---

###### 85. Che tipo di informazioni verrebbero loggate?

```javascript
fetch('https://www.website.com/api/user/1')
  .then(res => res.json())
  .then(res => console.log(res));
```

- A: Il risultato del metodo `fetch`.
- B: Il risultato della seconda invocazione del metodo `fetch`.
- C: Il risultato della callback nel precedente `.then()`.
- D: Sarebbe sempre undefined.

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Il valore di `res` nel secondo `.then` รจ uguale al valore restituito del precedente `.then`. Puoi continuare a concatenare i `.then` in questo modo, dove il valore viene passato al gestore successivo.

</p>
</details>

---

###### 86. Quale opzione รจ un modo per impostare `hasName` uguale a `true`, se non puoi passare `true` come argomento?

```javascript
function getName(name) {
  const hasName = //
}
```

- A: `!!name`
- B: `name`
- C: `new Boolean(name)`
- D: `name.length`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Con `!!name`, determiniamo se il valore di `name` รจ vero o falso. Se il nome รจ vero, cosa che vogliamo testare, `!name` restituisce `false`. 
`!false` (che รจ `!!name`) restituisce `true`.

Impostando `hasName` uguale a `name`, imposti `hasName` uguale a qualsiasi valore passato alla funzione `getName`, non il valore booleano `true`.

`new Boolean(true)` restituisce un oggetto wrapper, non il valore booleano stesso.

`name.length` restituisce la lunghezza dell'argomento passato, non se รจ `true`.

</p>
</details>

---

###### 87. Qual รจ l'output?

```javascript
console.log('I want pizza'[0]);
```

- A: `"""`
- B: `"I"`
- C: `SyntaxError`
- D: `undefined`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Per ottenere un carattere in un indice specifico di una stringa, puoi usare la notazione tra parentesi. Il primo carattere nella stringa ha indice 0 e cosรฌ via. In questo caso, vogliamo ottenere l'elemento con indice 0, il carattere `"I'`, che viene loggato.

Tieni presente che questo metodo non รจ supportato in IE7 e versioni precedenti. In tal caso, usa `.charAt()`.

</p>
</details>

---

###### 88. Qual รจ l'output?

```javascript
function sum(num1, num2 = num1) {
  console.log(num1 + num2);
}

sum(10);
```

- A: `NaN`
- B: `20`
- C: `ReferenceError`
- D: `undefined`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

ร possibile impostare il valore di un parametro predefinito uguale a un altro parametro della funzione, purchรฉ sia stato definito _prima_ del parametro predefinito. Passiamo il valore `10` alla funzione `sum`. Se la funzione `sum` riceve solo 1 argomento, significa che il valore di `num2` non รจ passato e il valore di `num1` รจ uguale al valore passato `10` in questo caso. Il valore predefinito di `num2` รจ il valore di `num1`, che รจ `10`. `num1 + num2` restituisce `20`.

Se stai cercando di impostare il valore di un parametro predefinito uguale a un parametro che รจ definito _dopo_ (a destra), il valore del parametro non รจ stato ancora inizializzato, il che genererร? un errore.
</p>
</details>

---

###### 89. Qual รจ l'output?

```javascript
// module.js
export default () => 'Hello world';
export const name = 'Lydia';

// index.js
import * as data from './module';

console.log(data);
```

- A: `{ default: function default(), name: "Lydia" }`
- B: `{ default: function default() }`
- C: `{ default: "Hello world", name: "Lydia" }`
- D: Global object of `module.js`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Con la sintassi `import * as name`, importiamo _tutte le esportazioni_ dal file `module.js` nel file `index.js` come nuovo oggetto chiamato `data`. Nel file `module.js` ci sono due esportazioni: l'esportazione predefinita e un'esportazione denominata. L'esportazione predefinita รจ una funzione che restituisce la stringa `"Hello World"`, e l'esportazione denominata รจ una variabile chiamata `name` che ha il valore della stringa `"Lydia"`.

L'oggetto `data` ha una proprietร? `default` per l'esportazione predefinita, altre proprietร? hanno i nomi delle esportazioni e i loro valori corrispondenti.

</p>
</details>

---

###### 90. Qual รจ l'output?

```javascript
class Person {
  constructor(name) {
    this.name = name;
  }
}

const member = new Person('John');
console.log(typeof member);
```

- A: `"class"`
- B: `"function"`
- C: `"object"`
- D: `"string"`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Le classi sono come caramelle sintattiche. L'equivalente della classe `Person` come funzione sarebbe:

```javascript
function Person() {
  this.name = name;
}
```

Instanziando un costruttore con `new` si ottiene la creazione di un'istanza di `Person`, la chiave `typeof` restituisce `"object"`. `typeof member` restituisce `"object"`.

</p>
</details>

---

###### 91. Qual รจ l'output?

```javascript
let newList = [1, 2, 3].push(4);

console.log(newList.push(5));
```

- A: `[1, 2, 3, 4, 5]`
- B: `[1, 2, 3, 5]`
- C: `[1, 2, 3, 4]`
- D: `Error`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

Il metodo `.push` restituisce la _nuova lunghezza_ dell'array, non l'array stesso! Impostando `newList` uguale a `[1, 2, 3].push(4)`, settiamo `newList` uguale alla nuova lunghezza dell'array: `4`.

Quindi quando proviamo a usare il metodo `.push` su `newList` poichรฉ `newList` รจ il valore numerico `4`, non possiamo usare il metodo `.push` e viene generato un TypeError.

</p>
</details>

---

###### 92. Qual รจ l'output?

```javascript
function giveLydiaPizza() {
  return 'Here is pizza!';
}

const giveLydiaChocolate = () =>
  "Here's chocolate... now go hit the gym already.";

console.log(giveLydiaPizza.prototype);
console.log(giveLydiaChocolate.prototype);
```

- A: `{ constructor: ...}` `{ constructor: ...}`
- B: `{}` `{ constructor: ...}`
- C: `{ constructor: ...}` `{}`
- D: `{ constructor: ...}` `undefined`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

Le funzioni regolari, come la funzione `giveLydiaPizza`, hanno una proprietร? `prototipo`, che รจ un oggetto (prototype object) con un `costruttore`. Tuttavia, le arrow functions, come la funzione `giveLydiaChocolate`, non hanno una proprietร? `prototype`. Viene quindi restituito `undefined` quando si tenta di accedere alla proprietร? `prototype` usando `giveLydiaChocolate.prototype`.
</p>
</details>

---

###### 93. Qual รจ l'output?

```javascript
const person = {
  name: 'Lydia',
  age: 21,
};

for (const [x, y] of Object.entries(person)) {
  console.log(x, y);
}
```

- A: `name` `Lydia` e `age` `21`
- B: `["name", "Lydia"]` e `["age", 21]`
- C: `["name", "age"]` e `undefined`
- D: `Error`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

`Object.entries(person)` restituisce un array di array nidificati, contenente le chiavi e gli oggetti:

`[ [ 'name', 'Lydia' ], [ 'age', 21 ] ]`

Usando il ciclo `for-of`, possiamo scorrere ogni elemento nell'array, i sottoarray in questo caso. Possiamo destrutturare i sottoarray istantaneamente nel ciclo for-of, usando `const [x, y]`. `x` รจ uguale al primo elemento, `y` รจ uguale al secondo elemento.

Il primo sottoarray รจ `[ "name", "Lydia" ]`, con `x` uguale a `"name"`, e `y` uguale a `"Lydia"`, che vengono loggati.
Il secondo sottoarray รจ `[ "age", 21 ]`, con `x` uguale a `"age"`, e `y` uguale a `21`, che vengono loggati.

</p>
</details>

---

###### 94. Qual รจ l'output?

```javascript
function getItems(fruitList, ...args, favoriteFruit) {
  return [...fruitList, ...args, favoriteFruit]
}

getItems(["banana", "apple"], "pear", "orange")
```

- A: `["banana", "apple", "pear", "orange"]`
- B: `[["banana", "apple"], "pear", "orange"]`
- C: `["banana", "apple", ["pear"], "orange"]`
- D: `SyntaxError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

`...args` รจ un parametro rest. Il valore del parametro rest รจ un array contenente tutti gli argomenti, **e puรฒ essere solo l'ultimo parametro**! In questo esempio, il parametro rest รจ in seconda posizione. Questo non รจ possibile e genererร? un errore di sintassi.

```javascript
function getItems(fruitList, favoriteFruit, ...args) {
  return [...fruitList, ...args, favoriteFruit];
}

getItems(['banana', 'apple'], 'pear', 'orange');
```

L'esempio qui sopra invece funziona e restituisce l'array `[ 'banana', 'apple', 'orange', 'pear' ]`

</p>
</details>

---

###### 95. Qual รจ l'output?

```javascript
function nums(a, b) {
  if (a > b) console.log('a is bigger');
  else console.log('b is bigger');
  return
  a + b;
}

console.log(nums(4, 2));
console.log(nums(1, 2));
```

- A: `a is bigger`, `6` and `b is bigger`, `3`
- B: `a is bigger`, `undefined` and `b is bigger`, `undefined`
- C: `undefined` and `undefined`
- D: `SyntaxError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

In JavaScript, non _รจ necessario_ scrivere il punto e virgola (`;`) in modo esplicito poichรฉ il motore JavaScript li aggiunge comunque dopo le istruzioni. 
Questo procedimento รจ chiamato **Automatic Semicolon Insertion**. Un'istruzione puรฒ ad esempio essere una variabile o parole chiave come `throw`, `return`, `break`, ecc.

Qui, abbiamo scritto un'istruzione di `return` e un altro valore `a + b` su una _nuova riga_. Tuttavia, trattandosi di una nuova linea, il motore non sa che in realtร? รจ il valore che volevamo restituire. Invece, ha aggiunto automaticamente un punto e virgola dopo `return`. 

Potresti considerare ad esempio:

```javascript
return;
a + b;
```

`a + b` non viene mai raggiunto, poichรฉ la funzione smette di funzionare dopo la parola chiave `return`. 
Se non viene restituito alcun valore, come qui, la funzione restituisce `undefined`. Nota: non c'รจ un inserimento automatico dopo le istruzioni `if/else`!

</p>
</details>

---

###### 96. Qual รจ l'output?

```javascript
class Person {
  constructor() {
    this.name = 'Lydia';
  }
}

Person = class AnotherPerson {
  constructor() {
    this.name = 'Sarah';
  }
};

const member = new Person();
console.log(member.name);
```

- A: `"Lydia"`
- B: `"Sarah"`
- C: `Error: cannot redeclare Person`
- D: `SyntaxError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Possiamo impostare classi uguali ad altre classi/costruttori di funzioni. In questo caso, impostiamo `Person` uguale a `AnotherPerson`. Il name su questo costruttore รจ `Sarah`, quindi la proprietร? del nome di`Person` sulla nuova istanza `member`  รจ `"Sarah"`.

</p>
</details>

---

###### 97. Qual รจ l'output?

```javascript
const info = {
  [Symbol('a')]: 'b',
};

console.log(info);
console.log(Object.keys(info));
```

- A: `{Symbol('a'): 'b'}` e `["{Symbol('a')"]`
- B: `{}` e `[]`
- C: `{ a: "b" }` e `["a"]`
- D: `{Symbol('a'): 'b'}` e `[]`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

Un simbolo non รจ _enumerabile_. Il metodo Object.keys restituisce tutte le proprietร? _enumerabili_ su un oggetto. Il simbolo non sarร? visibile e verrร? restituito un array vuoto. Quando si logga l'intero oggetto, tutte le proprietร? saranno visibili, anche quelle non enumerabili.

Questa รจ una delle tante qualitร? di un simbolo: oltre a rappresentare un valore del tutto univoco (che evita collisioni accidentali di nomi sugli oggetti, ad esempio quando si lavora con 2 librerie che vogliono aggiungere proprietร? allo stesso oggetto), puoi anche "nascondere" proprietร? sugli oggetti in questo modo (anche se non del tutto. Puoi comunque accedere ai simboli usando il metodo `Object.getOwnPropertySymbols()`).

</p>
</details>

---

###### 98. Qual รจ l'output?

```javascript
const getList = ([x, ...y]) => [x, y]
const getUser = user => { name: user.name, age: user.age }

const list = [1, 2, 3, 4]
const user = { name: "Lydia", age: 21 }

console.log(getList(list))
console.log(getUser(user))
```

- A: `[1, [2, 3, 4]]` e `SyntaxError`
- B: `[1, [2, 3, 4]]` e `{ name: "Lydia", age: 21 }`
- C: `[1, 2, 3, 4]` e `{ name: "Lydia", age: 21 }`
- D: `Error` e `{ name: "Lydia", age: 21 }`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

La funzione `getList` riceve un array come argomento. Tra le parentesi della funzione `getList`, destrutturiamo subito questo array. Esempio:

`[x, ...y] = [1, 2, 3, 4]`

Con il parametro rest `...y`, mettiamo tutti gli argomenti "rimanenti" in un array. Gli argomenti rimanenti sono `2`, `3` e `4` in questo caso. 
Il valore di `y` รจ un array, contenente tutti i parametri rimanenti. Il valore di `x` รจ uguale a `1` in questo caso, quindi quando facciamo un console.log di `[x, y]`, viene loggato `[1, [2, 3, 4]]`.

La funzione `getUser` riceve un oggetto. Con le arrow functions, non _รจ necessario_ scrivere parentesi graffe se restituiamo solo un valore. Tuttavia, se vuoi restituire istantaneamente un _oggetto_ da una arrow function, devi scriverlo tra parentesi tonde, altrimenti tutto ciรฒ che si trova tra le due parentesi graffe verrร? interpretato come un'istruzione di blocco. In questo caso il codice tra parentesi non รจ un codice JavaScript valido, quindi viene generato un `SyntaxError`.

La seguente funzione avrebbe restituito un oggetto:

`const getUser = user => ({ name: user.name, age: user.age })`

</p>
</details>

---

###### 99. Qual รจ l'output?

```javascript
const name = 'Lydia';

console.log(name());
```

- A: `SyntaxError`
- B: `ReferenceError`
- C: `TypeError`
- D: `undefined`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

La variabile `name` contiene il valore di una stringa, che non รจ una funzione, quindi non puรฒ essere invocata.

I TypeErrors vengono generati quando un valore non รจ del tipo previsto. JavaScript "prevede" che `name` รจ una funzione poichรฉ stiamo cercando di invocarla. In realtร? รจ una stringa, quindi viene generato un TypeError: name is not a function!

I SyntaxErrors vengono generati quando si scrive qualcosa che non รจ valido in JavaScript, ad esempio quando si scrive la parola `return` come `rerun`.
I ReferenceErrors vengono generati quando JavaScript non รจ in grado di trovare un riferimento a un valore a cui stai tentando di accedere.

</p>
</details>

---

###### 100. Qual รจ il valore dell'output?

```javascript
// ๐โจ This is my 100th question! โจ๐

const output = `${[] && 'Im'}possible!
You should${'' && `n't`} see a therapist after so much JavaScript lol`;
```

- A: `possible! You should see a therapist after so much JavaScript lol`
- B: `Impossible! You should see a therapist after so much JavaScript lol`
- C: `possible! You shouldn't see a therapist after so much JavaScript lol`
- D: `Impossible! You shouldn't see a therapist after so much JavaScript lol`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

`[]` รจ un valore vero. Con l'operatore `&&`, verrร? restituito il valore di destra se il valore di sinistra รจ un valore reale. In questo caso, il valore di sinistra `[]` รจ un valore vero, quindi `"Im'` viene restituito.

`""` รจ un valore falso. Se il valore di sinistra รจ falso, non viene restituito nulla. `n't` quindi non viene restituito.

</p>
</details>

---

###### 101. Qual รจ il valore dell'output?

```javascript
const one = false || {} || null;
const two = null || false || '';
const three = [] || 0 || true;

console.log(one, two, three);
```

- A: `false` `null` `[]`
- B: `null` `""` `true`
- C: `{}` `""` `[]`
- D: `null` `null` `true`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Con l'operatore `||` possiamo restituire il primo operando veritiero. Se tutti i valori sono falsi, viene restituito l'ultimo operando.

`(false || {} || null)`: l'oggetto vuoto `{}` รจ un valore veritiero. Questo รจ il primo (e unico) valore veritiero, che viene restituito. `one` รจ uguale a `{}`.

`(null || false || "")`: tutti gli operandi sono valori falsi. Ciรฒ significa che viene restituito l'ultimo operando, `""`. `two` รจ uguale a `""`.

`([] || 0 || "")`: l'array vuoto`[]` รจ un valore veritiero. Questo รจ il primo valore veritiero, che viene restituito. `three` รจ uguale a `[]`.

</p>
</details>

---

###### 102. Qual รจ il valore dell'output?

```javascript
const myPromise = () => Promise.resolve('I have resolved!');

function firstFunction() {
  myPromise().then(res => console.log(res));
  console.log('second');
}

async function secondFunction() {
  console.log(await myPromise());
  console.log('second');
}

firstFunction();
secondFunction();
```

- A: `I have resolved!`, `second` e `I have resolved!`, `second`
- B: `second`, `I have resolved!` e `second`, `I have resolved!`
- C: `I have resolved!`, `second` e `second`, `I have resolved!`
- D: `second`, `I have resolved!` e `I have resolved!`, `second`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

Con una promise, in pratica diciamo _Voglio eseguire questa funzione, ma per ora la metto da parte mentre รจ in esecuzione poichรฉ ciรฒ potrebbe richiedere del tempo. Solo quando un determinato valore viene risolto (o rifiutato) e quando lo stack di chiamate รจ vuoto, voglio utilizzare questo valore._

Possiamo ottenere questo valore sia con `.then` che con la chiave `await` in una funzione `async`. Sebbene possiamo ottenere il valore di una promise sia con `.then` che con `await`, funzionano in modo leggermente diverso.

Nella `first Function`, abbiamo (piรน o meno) messo da parte la funzione myPromise mentre era in esecuzione, ma abbiamo continuato a eseguire l'altro codice, che in questo caso รจ `console.log('second')`. Quindi, la funzione รจ stata risolta con la stringa `I have resolved`, che รจ stata quindi loggata dopo aver visto che lo stack di chiamate era vuoto.

Con await in `secondFunction`, mettiamo letteralmente in pausa l'esecuzione di una funzione asincrona fino a quando il valore non รจ stato risolto prima di passare alla riga successiva.

Ciรฒ significa che ha aspettato che `myPromise` si risolvesse con il valore `I have resolved`, e solo allora, siamo passati alla riga successiva e `second` รจ stato loggato.

</p>
</details>

---

###### 103. Qual รจ il valore dell'output?

```javascript
const set = new Set();

set.add(1);
set.add('Lydia');
set.add({ name: 'Lydia' });

for (let item of set) {
  console.log(item + 2);
}
```

- A: `3`, `NaN`, `NaN`
- B: `3`, `7`, `NaN`
- C: `3`, `Lydia2`, `[object Object]2`
- D: `"12"`, `Lydia2`, `[object Object]2`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

L'operatore `+` non viene utilizzato solo per aggiungere valori numerici, ma possiamo anche usarlo per concatenare stringhe. Ogni volta che il motore JavaScript vede che uno o piรน valori non sono un numero, forza il numero in una stringa.

Il primo รจ `1`, che รจ un valore numerico. `1 + 2` restituisce il numero 3.

Tuttavia, la seconda รจ una stringa `"Lydia"`. `"Lydia"` รจ una stringa e `2` รจ un numero: `2` viene forzato in una stringa. `"Lydia"` e `"2"` vengono concatenati, il che risulta nella stringa `"Lydia2"`.

`{ name: "Lydia" }` รจ un oggetto. Nรฉ un numero nรฉ un oggetto sono una stringa, quindi li rende stringhe entrambi. Ogni volta che stringhiamo un oggetto regolare, diventa `"[object Object]"`. `"[object Object]"` concatenato con `2` diventa `"[object Object]"`.

</p>
</details>

---

###### 104. Qual รจ il suo valore?

```javascript
Promise.resolve(5);
```

- A: `5`
- B: `Promise {<pending>: 5}`
- C: `Promiseย?{<fulfilled>: 5}`
- D: `Error`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Possiamo passare a `Promise.resolve` qualsiasi tipo di valore desideriamo, sia una promise che una non-promise. Il metodo stesso restituisce una promise con il valore risolto (`<fulfilled>`). Se si passa una funzione regolare, sarร? una promise risolta con un valore regolare. Se mandi una promise, sarร? una promise risolta con il valore risolto di quella promise passata.

In questo caso, abbiamo appena passato il valore numerico `5`. Restituisce una promise risolta con il valore `5`.

</p>
</details>

---

###### 105. Qual รจ il suo valore?

```javascript
function compareMembers(person1, person2 = person) {
  if (person1 !== person2) {
    console.log('Not the same!');
  } else {
    console.log('They are the same!');
  }
}

const person = { name: 'Lydia' };

compareMembers(person);
```

- A: `Not the same!`
- B: `They are the same!`
- C: `ReferenceError`
- D: `SyntaxError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Gli oggetti vengono passati per riferimento. Quando controlliamo gli oggetti per strict equality (`===`), stiamo confrontando i loro riferimenti.

Abbiamo impostato il valore predefinito per `person2` uguale all'oggetto `person` e abbiamo passato l'oggetto `person` come valore per `person1`.

Ciรฒ significa che entrambi i valori hanno un riferimento allo stesso punto in memoria, quindi sono uguali.

Il blocco di codice nell'istruzione `else` viene eseguito e `They are the same!` viene loggato.

</p>
</details>

---

###### 106. Qual รจ il suo valore?

```javascript
const colorConfig = {
  red: true,
  blue: false,
  green: true,
  black: true,
  yellow: false,
};

const colors = ['pink', 'red', 'blue'];

console.log(colorConfig.colors[1]);
```

- A: `true`
- B: `false`
- C: `undefined`
- D: `TypeError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

In JavaScript, abbiamo due modi per accedere alle proprietร? di un oggetto: le bracket notation o le dot notation. In questo esempio, utilizziamo la notazione con il punto (`colorConfig.colors`) invece della notazione tra parentesi (`colorConfig["colors"]`).

Con la notazione del punto, JavaScript tenta di trovare la proprietร? sull'oggetto con quel nome esatto. In questo esempio, JavaScript tenta di trovare una proprietร? chiamata `colors` sull'oggetto `colorConfig`. Non esiste una proprietร? chiamata `colors`, quindi restituisce `undefined`. Quando proviamo ad accedere al valore del primo elemento usando `[1]`, non possiamo farlo su un valore che รจ `undefined`, quindi genera un `TypeError`: `Cannot read property '1' of undefined`.

JavaScript interpreta (o decomprime) le istruzioni. Quando usiamo la notazione tra parentesi, vede la prima parentesi aperta `[` e continua finchรฉ non trova la parentesi chiusa `]`. Solo allora valuterร? la dichiarazione. Se avessimo usato `colorConfig[colors[1]]`, avrebbe restituito il valore della proprietร? `red` sull'oggetto `colorConfig`.

</p>
</details>

---

###### 107. Qual รจ il suo valore?

```javascript
console.log('โค๏ธ' === 'โค๏ธ');
```

- A: `true`
- B: `false`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Le emoji sono unicode. L'unicode per l'emoji del cuore รจ `"U+2764 U+FE0F"`. Questi sono sempre gli stessi per gli stessi emoji, stiamo confrontando due stringhe uguali tra loro, e quindi restituisce true.

</p>
</details>

---

###### 108. Quale di questi metodi modifica l'array originale?

```javascript
const emojis = ['โจ', '๐ฅ', '๐'];

emojis.map(x => x + 'โจ');
emojis.filter(x => x !== '๐ฅ');
emojis.find(x => x !== '๐ฅ');
emojis.reduce((acc, cur) => acc + 'โจ');
emojis.slice(1, 2, 'โจ');
emojis.splice(1, 2, 'โจ');
```

- A: `All of them`
- B: `map` `reduce` `slice` `splice`
- C: `map` `slice` `splice`
- D: `splice`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

Con il metodo `splice` modifichiamo l'array originale cancellando, sostituendo o aggiungendo elementi. In questo caso, abbiamo rimosso 2 elementi dall'indice 1 (abbiamo rimosso `'๐ฅ'` e `'๐'`) e aggiunto invece l'emoji โจ.

`map`, `filter` e `slice` restituiscono un nuovo array, `find` restituisce un elemento e `reduce` restituisce un valore ridotto.
</p>
</details>

---

###### 109. Qual รจ l'output?

```javascript
const food = ['๐', '๐ซ', '๐ฅ', '๐'];
const info = { favoriteFood: food[0] };

info.favoriteFood = '๐';

console.log(food);
```

- A: `['๐', '๐ซ', '๐ฅ', '๐']`
- B: `['๐', '๐ซ', '๐ฅ', '๐']`
- C: `['๐', '๐', '๐ซ', '๐ฅ', '๐']`
- D: `ReferenceError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Impostiamo il valore della proprietร? `favoriteFood` sull'oggetto `info` uguale alla stringa con l'emoji della pizza, `'๐'`. Una stringa รจ un tipo di dati primitivo. In JavaScript, i tipi di dati primitivi non interagiscono per riferimento.

In JavaScript, i tipi di dati primitivi (tutto ciรฒ che non รจ un oggetto) interagiscono per _value_. In questo caso, impostiamo il valore della proprietร? `favoriteFood` sull'oggetto `info` uguale al valore del primo elemento nell'array `food`, in questo caso la stringa con l'emoji della pizza (`'๐'`). Una stringa รจ un tipo di dati primitivo e interagisce per valore (vedi il mio [blogpost](https://www.theavocoder.com/complete-javascript/2018/12/21/by-value-vs-by-reference) se sei interessato a saperne di piรน).

Quindi, cambiamo il valore della proprietร? `favoriteFood` sull'oggetto `info`. L'array `food` non รจ cambiato, poichรฉ il valore di `favoriteFood` era semplicemente una _copia_ del valore del primo elemento nell'array e non ha un riferimento allo stesso punto in memoria dell'elemento su ` food[0]`. Quando logghiamo food, รจ ancora l'array originale, `['๐', '๐ซ', '๐ฅ', '๐']`.
</p>
</details>

---

###### 110. Cosa fa questo metodo?

```javascript
JSON.parse();
```

- A: converte JSON in un valore JavaScript
- B: converte un oggetto JavaScript in JSON
- C: converte qualsiasi valore JavaScript in JSON
- D: converte JSON in un oggetto solo JavaScript

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Con il metodo `JSON.parse()`, possiamo analizzare la stringa JSON come un valore JavaScript.

```javascript
// Stringhiamo un numero in un JSON valido, quindi analizziamo la stringa JSON come valore JavaScript:
const jsonNumber = JSON.stringify(4); // '4'
JSON.parse(jsonNumber); // 4

// Stringhiamo un array in un JSON valido, quindi analizziamo la stringa JSON come valore JavaScript:
const jsonArray = JSON.stringify([1, 2, 3]); // '[1, 2, 3]'
JSON.parse(jsonArray); // [1, 2, 3]

// Stringhiamo un object in un JSON valido, quindi analizziamo la stringa JSON come valore JavaScript:
const jsonArray = JSON.stringify({ name: 'Lydia' }); // '{"name":"Lydia"}'
JSON.parse(jsonArray); // { name: 'Lydia' }
```

</p>
</details>

---

###### 111. Qual รจ l'output?

```javascript
let name = 'Lydia';

function getName() {
  console.log(name);
  let name = 'Sarah';
}

getName();
```

- A: Lydia
- B: Sarah
- C: `undefined`
- D: `ReferenceError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

Ogni funzione ha il proprio _contesto di esecuzione_ (o _ambito_). La funzione `getName` cerca prima all'interno del proprio contesto (scope) per vedere se contiene la variabile `name` a cui stiamo cercando di accedere. In questo caso, la funzione `getName` contiene la propria variabile `name` perchรฉ dichiariamo la variabile `name` con la chiave `let`, e con il valore di `'Sarah'`.

Le variabili con la chiave `let` (e `const`) vengono sollevate, ma a differenza di `var`, non vengono <i>inizializzate</i>. Non sono quindi accessibili prima della riga in cui le dichiariamo (inizializziamo). Questa รจ chiamata "temporal dead zone". Quando proviamo ad accedere alle variabili prima che vengano dichiarate, JavaScript genera un `ReferenceError`.

Se non avessimo dichiarato la variabile `name` all'interno della funzione `getName`, JavaScript avrebbe esaminato la _scope chain_. Lo scope esterno ha una variabile chiamata `name` con il valore di `Lydia`. In tal caso, avrebbe loggato "Lydia".

```javascript
let name = 'Lydia';

function getName() {
  console.log(name);
}

getName(); // Lydia
```

</p>
</details>

---

###### 112. Qual รจ l'output?

```javascript
function* generatorOne() {
  yield ['a', 'b', 'c'];
}

function* generatorTwo() {
  yield* ['a', 'b', 'c'];
}

const one = generatorOne();
const two = generatorTwo();

console.log(one.next().value);
console.log(two.next().value);
```

- A: `a` e `a`
- B: `a` e `undefined`
- C: `['a', 'b', 'c']` e `a`
- D: `a` e `['a', 'b', 'c']`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Con la parola chiave `yield`, otteniamo valori in una funzione generatore. Con la chiave `yield*`, possiamo produrre valori da un'altra funzione del generatore, o da un oggetto iterabile (per esempio un array).

In `generatorOne`, produciamo l'intero array `['a', 'b', 'c']` usando la parola chiave `yield`. Il valore della proprietร? `value` sull'oggetto restituito dal metodo `next` su `one` (`one.next().value`) รจ uguale all'intero array `['a', 'b', 'c']`.

```javascript
console.log(one.next().value); // ['a', 'b', 'c']
console.log(one.next().value); // undefined
```

In `generatorTwo`, utilizziamo la parola chiave `yield*`. Ciรฒ significa che il primo valore ottenuto รจ `two`, ed รจ uguale al primo valore ottenuto nell'iteratore. L'iteratore รจ l'array `['a', 'b', 'c']`. Il primo valore ottenuto รจ `a`, quindi la prima volta che chiamiamo `two.next().value`, viene restituito `a`.

```javascript
console.log(two.next().value); // 'a'
console.log(two.next().value); // 'b'
console.log(two.next().value); // 'c'
console.log(two.next().value); // undefined
```

</p>
</details>

---

###### 113. Qual รจ l'output?

```javascript
console.log(`${(x => x)('I love')} to program`);
```

- A: `I love to program`
- B: `undefined to program`
- C: `${(x => x)('I love') to program`
- D: `TypeError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Le espressioni all'interno dei template literals vengono valutate per prime. Ciรฒ significa che la stringa conterrร? il valore restituito dell'espressione, in questo caso la funzione immediatamente invocata `(x => x)('I love')`. Passiamo il valore `'I love'` come argomento alla funzione freccia `x => x`. `x` รจ uguale a `'I love'`, che viene restituito. Ciรฒ si traduce in `I love to program`.

</p>
</details>

---

###### 114. Cosa accadrร??

```javascript
let config = {
  alert: setInterval(() => {
    console.log('Alert!');
  }, 1000),
};

config = null;
```

- A: La callback `setInterval` non verrร? invocata
- B: La callback `setInterval` viene invocata una volta
- C: La callback `setInterval` verrร? comunque chiamata ogni secondo
- D: Non abbiamo mai invocato `config.alert()`, config รจ `null`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Normalmente quando impostiamo oggetti uguali a `null`, quegli oggetti vengono _garbage collected_ poichรฉ non c'รจ piรน alcun riferimento a quell'oggetto. Tuttavia, poichรฉ la funzione di callback all'interno di `setInterval` รจ una funzione freccia (quindi legata all'oggetto `config`), la funzione di callback mantiene ancora un riferimento all'oggetto `config`.
Finchรฉ c'รจ un riferimento, l'oggetto non verrร? raccolto.
Poichรฉ si tratta di un intervallo, impostare `config` su `null` o `delete`-ing `config.alert` non raccoglierร? l'intervallo, quindi l'intervallo verrร? comunque chiamato.
Dovrebbe essere cancellato con `clearInterval(config.alert)` per rimuoverlo dalla memoria.
Dal momento che non รจ stato cancellato, la funzione di callback `setInterval` verrร? comunque invocata ogni 1000 ms (1 s).

</p>
</details>

---

###### 115. Quali metodi restituiranno il valore `'Hello world!'`?

```javascript
const myMap = new Map();
const myFunc = () => 'greeting';

myMap.set(myFunc, 'Hello world!');

//1
myMap.get('greeting');
//2
myMap.get(myFunc);
//3
myMap.get(() => 'greeting');
```

- A: 1
- B: 2
- C: 2 e 3
- D: Tutti

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Quando si aggiunge una coppia chiave/valore usando il metodo `set`, la chiave sarร? il valore del primo argomento passato alla funzione `set`, e il valore sarร? il secondo argomento. La chiave รจ _function_ `() => 'greeting'` in questo caso, e il valore `'Hello world'`. `myMap` ora รจ `{ () => 'greeting' => 'Hello world!' }`.

1 รจ sbagliato, poichรฉ la chiave non รจ `'greeting'` ma `() => 'greeting'`.
3 รจ sbagliato, poichรฉ stiamo creando una nuova funzione passandola come parametro al metodo `get`. L'oggetto interagisce per _reference_. Le funzioni sono oggetti, che รจ il motivo per cui due funzioni non sono mai rigorosamente uguali, anche se identiche: hanno un riferimento a un punto diverso della memoria.

</p>
</details>

---

###### 116. Qual รจ l'output?

```javascript
const person = {
  name: 'Lydia',
  age: 21,
};

const changeAge = (x = { ...person }) => (x.age += 1);
const changeAgeAndName = (x = { ...person }) => {
  x.age += 1;
  x.name = 'Sarah';
};

changeAge(person);
changeAgeAndName();

console.log(person);
```

- A: `{name: "Sarah", age: 22}`
- B: `{name: "Sarah", age: 23}`
- C: `{name: "Lydia", age: 22}`
- D: `{name: "Lydia", age: 23}`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Entrambe le funzioni `changeAge` e `changeAgeAndName` hanno un parametro predefinito, ovvero un oggetto _appena_ creato `{ ...person }`. Questo oggetto ha copie di tutte le chiavi/valori nell'oggetto `person`.

Per prima cosa, invochiamo la funzione `changeAge` e passiamo l'oggetto `person` come argomento. Questa funzione aumenta il valore della proprietร? `age` di 1. `person` ora รจ `{ name: "Lydia", age: 22 }`.

Quindi, invochiamo la funzione `changeAgeAndName`, tuttavia non passiamo un parametro. Invece, il valore di `x` รจ uguale a un _nuovo_ oggetto: `{ ...person }`. Poichรฉ si tratta di un nuovo oggetto, non influisce sui valori delle proprietร? sull'oggetto `person`. `person` รจ ancora uguale a `{ name: "Lydia", age: 22 }`.
</p>
</details>

---

###### 117. Quale delle seguenti opzioni restituirร? `6`?

```javascript
function sumValues(x, y, z) {
  return x + y + z;
}
```

- A: `sumValues([...1, 2, 3])`
- B: `sumValues([...[1, 2, 3]])`
- C: `sumValues(...[1, 2, 3])`
- D: `sumValues([1, 2, 3])`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Con l'operatore spread `...`, possiamo _distribuire_ gli iterabili come singoli elementi. La funzione `sumValues` riceve tre argomenti: `x`, `y` e `z`. `...[1, 2, 3]` risulterร? in `1, 2, 3`, che passiamo alla funzione `sumValues`.

</p>
</details>

---

###### 118. Qual รจ l'output?

```javascript
let num = 1;
const list = ['๐ฅณ', '๐ค?', '๐ฅฐ', '๐คช'];

console.log(list[(num += 1)]);
```

- A: `๐ค?`
- B: `๐ฅฐ`
- C: `SyntaxError`
- D: `ReferenceError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Con l'operando `+=`, stiamo incrementando il valore di `num` di `1`. `num` aveva il valore iniziale `1`, quindi `1 + 1` รจ `2`. L'elemento sul secondo indice nell'array `list` รจ ๐ฅฐ, `console.log(list[2])` stampa ๐ฅฐ.

</p>
</details>

---

###### 119. Qual รจ l'output?

```javascript
const person = {
  firstName: 'Lydia',
  lastName: 'Hallie',
  pet: {
    name: 'Mara',
    breed: 'Dutch Tulip Hound',
  },
  getFullName() {
    return `${this.firstName} ${this.lastName}`;
  },
};

console.log(person.pet?.name);
console.log(person.pet?.family?.name);
console.log(person.getFullName?.());
console.log(member.getLastName?.());
```

- A: `undefined` `undefined` `undefined` `undefined`
- B: `Mara` `undefined` `Lydia Hallie` `ReferenceError`
- C: `Mara` `null` `Lydia Hallie` `null`
- D: `null` `ReferenceError` `null` `ReferenceError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Con l'operatore di concatenamento opzionale `?.`, non รจ piรน necessario verificare esplicitamente se i valori annidati piรน profondi sono validi o meno. Se stiamo cercando di accedere a una proprietร? su un valore `undefined` o `null` (_nullish_), l'espressione va in cortocircuito e restituisce `undefined`.

`person.pet?.name`: `person` ha una proprietร? denominata `pet`: `person.pet` non รจ nullo. Ha una proprietร? chiamata `name` e restituisce `Mara`.
`person.pet?.family?.name`: `person` ha una proprietร? denominata `pet`: `person.pet` non รจ nullo. `pet` _non_ ha una proprietร? chiamata `family`, `person.pet.family` รจ nullo. L'espressione restituisce `undefined`.
`person.getFullName?.()`: `person` ha una proprietร? denominata `getFullName`: `person.getFullName()` non รจ nullo e puรฒ essere invocato, il che restituisce `Lydia Hallie`.
`member.getLastName?.()`: la variabile `member` non esiste quindi viene generato un `ReferenceError`!

</p>
</details>

---

###### 120. Qual รจ l'output?

```javascript
const groceries = ['banana', 'apple', 'peanuts'];

if (groceries.indexOf('banana')) {
  console.log('We have to buy bananas!');
} else {
  console.log(`We don't have to buy bananas!`);
}
```

- A: We have to buy bananas!
- B: We don't have to buy bananas
- C: `undefined`
- D: `1`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Abbiamo passato la condizione `groceries.indexOf("banana")` all'istruzione if. `groceries.indexOf("banana")` restituisce `0`, che รจ un valore falso. Poichรฉ la condizione nell'istruzione if รจ falsa, il codice nel blocco `else` viene eseguito e `We don't have to buy bananas!` viene registrato.

</p>
</details>

---

###### 121. Qual รจ l'output?

```javascript
const config = {
  languages: [],
  set language(lang) {
    return this.languages.push(lang);
  },
};

console.log(config.language);
```

- A: `function language(lang) { this.languages.push(lang }`
- B: `0`
- C: `[]`
- D: `undefined`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

Il metodo `language` รจ un `setter`. I setter non detengono un valore effettivo, il loro scopo รจ _modificare_ le proprietร?. Quando si chiama un metodo `setter`, viene restituito `undefined`.

</p>
</details>

---

###### 122. Qual รจ l'output?

```javascript
const name = 'Lydia Hallie';

console.log(!typeof name === 'object');
console.log(!typeof name === 'string');
```

- A: `false` `true`
- B: `true` `false`
- C: `false` `false`
- D: `true` `true`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

`typeof name` restituisce `"string"`. La stringa `"string"` รจ un valore veritiero, quindi `!typeof name` restituisce il valore booleano `false`. `false === "object"` e `false === "string"` restituiscono entrambi `false`.

(Se volessimo verificare se il tipo era (non)uguale a un certo tipo, avremmo dovuto scrivere `!==` invece di `!typeof`)
</p>
</details>

---

###### 123. Qual รจ l'output?

```javascript
const add = x => y => z => {
  console.log(x, y, z);
  return x + y + z;
};

add(4)(5)(6);
```

- A: `4` `5` `6`
- B: `6` `5` `4`
- C: `4` `function` `function`
- D: `undefined` `undefined` `6`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

La funzione `add` restituisce una arrow function, che restituisce una arrow function, che restituisce arrow function (mi segui ancora?). 
La prima funzione riceve un argomento `x` con il valore di `4`. Invochiamo la seconda funzione, che riceve un argomento `y` con il valore `5`. Quindi invochiamo la terza funzione, che riceve un argomento `z` con il valore `6`. Quando si tenta di accedere ai valori `x`, `y` e `z` all'interno dell'ultima arrow function, il motore JS risale la catena dell'ambito per trovare i valori per `x` e `y`. Questo restituisce `4` `5` `6`.

</p>
</details>

---

###### 124. Qual รจ l'output?

```javascript
async function* range(start, end) {
  for (let i = start; i <= end; i++) {
    yield Promise.resolve(i);
  }
}

(async () => {
  const gen = range(1, 3);
  for await (const item of gen) {
    console.log(item);
  }
})();
```

- A: `Promise {1}` `Promise {2}` `Promise {3}`
- B: `Promise {<pending>}` `Promise {<pending>}` `Promise {<pending>}`
- C: `1` `2` `3`
- D: `undefined` `undefined` `undefined`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

La funzione `range` restituisce un oggetto asincrono con promises per ogni elemento nell'intervallo che passiamo: `Promise{1}`, `Promise{2}`, `Promise{3}`. Impostiamo la variabile `gen` uguale all'oggetto asincrono, dopodichรฉ lo eseguiamo in loop usando un ciclo `for await ... of`. Impostiamo la variabile `item` uguale ai valori Promise restituiti: prima `Promise{1}`, poi `Promise{2}`, quindi `Promise{3}`. Poichรฉ stiamo _attendendo_ il valore di `item`, la promise risolta, vengono restituiti i _valori_ risolti delle promises: `1`, `2` e quindi `3`.

</p>
</details>

---

###### 125. Qual รจ l'output?

```javascript
const myFunc = ({ x, y, z }) => {
  console.log(x, y, z);
};

myFunc(1, 2, 3);
```

- A: `1` `2` `3`
- B: `{1: 1}` `{2: 2}` `{3: 3}`
- C: `{ 1: undefined }` `undefined` `undefined`
- D: `undefined` `undefined` `undefined`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

`myFunc` si aspetta un oggetto con le proprietร? `x`, `y` e `z` come argomento. Poichรฉ stiamo passando solo tre valori numerici separati (1, 2, 3) invece di un oggetto con le proprietร? `x`, `y` e `z` ({x: 1, y: 2, z: 3}), `x`, `y` e `z` hanno il loro valore predefinito di `undefined`.

</p>
</details>

---

###### 126. Qual รจ l'output?

```javascript
function getFine(speed, amount) {
  const formattedSpeed = new Intl.NumberFormat('en-US', {
    style: 'unit',
    unit: 'mile-per-hour'
  }).format(speed);

  const formattedAmount = new Intl.NumberFormat('en-US', {
    style: 'currency',
    currency: 'USD'
  }).format(amount);

  return `The driver drove ${formattedSpeed} and has to pay ${formattedAmount}`;
}

console.log(getFine(130, 300))
```

- A: The driver drove 130 and has to pay 300
- B: The driver drove 130 mph and has to pay \$300.00
- C: The driver drove undefined and has to pay undefined
- D: The driver drove 130.00 and has to pay 300.00

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Con il metodo `Intl.NumberFormat`, possiamo formattare i valori numerici in qualsiasi locale. Formattiamo il valore numerico `130` nella locale `en-US` come `unit` in `mile-per-hour`, che risulta in `130 mph`. Il valore numerico `300` nella locale `en-US` come `currency` in `USD` risulta in `$300.00`.

</p>
</details>

---

###### 127. Qual รจ l'output?

```javascript
const spookyItems = ['๐ป', '๐', '๐ธ'];
({ item: spookyItems[3] } = { item: '๐' });

console.log(spookyItems);
```

- A: `["๐ป", "๐", "๐ธ"]`
- B: `["๐ป", "๐", "๐ธ", "๐"]`
- C: `["๐ป", "๐", "๐ธ", { item: "๐" }]`
- D: `["๐ป", "๐", "๐ธ", "[object Object]"]`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Destrutturando gli oggetti, possiamo decomprimere i valori dall'oggetto di destra e assegnare il valore decompresso al valore dello stesso nome di proprietร? sull'oggetto di sinistra. In questo caso, stiamo assegnando il valore "๐" a `spookyItems[3]`. Ciรฒ significa che stiamo modificando l'array `spookyItems`, stiamo aggiungendo il "๐" ad esso. Quando facciamo console.log di `spookyItems`, `["๐ป", "๐", "๐ธ", "๐"]` viene loggato.

</p>
</details>

---

###### 128. Qual รจ l'output?

```javascript
const name = 'Lydia Hallie';
const age = 21;

console.log(Number.isNaN(name));
console.log(Number.isNaN(age));

console.log(isNaN(name));
console.log(isNaN(age));
```

- A: `true` `false` `true` `false`
- B: `true` `false` `false` `false`
- C: `false` `false` `true` `false`
- D: `false` `true` `false` `true`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Con il metodo `Number.isNaN`, puoi controllare se il valore passato รจ un _valore numerico_ e uguale a `NaN`. `name` non รจ un valore numerico, quindi `Number.isNaN(name)` restituisce `false`. `age` รจ un valore numerico, ma non รจ uguale a `NaN`, quindi `Numero.isNaN(age)` restituisce `false`.

Con il metodo `isNaN`, puoi verificare se il valore che passi non รจ un numero. `name` non รจ un numero, quindi `isNaN(name)` restituisce true. `age` รจ un numero, quindi `isNaN(age)` restituisce `false`.
</p>
</details>

---

###### 129. Qual รจ l'output?

```javascript
const randomValue = 21;

function getInfo() {
  console.log(typeof randomValue);
  const randomValue = 'Lydia Hallie';
}

getInfo();
```

- A: `"number"`
- B: `"string"`
- C: `undefined`
- D: `ReferenceError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

Le variabili dichiarate con la chiave `const` non sono referenziabili prima della loro inizializzazione: questa viene chiamata _temporal dead zone_. Nella funzione `getInfo`, la variabile `randomValue` ha lo scopo nell'ambito funzionale di `getInfo`. Nella riga in cui vogliamo registrare il valore di `typeof randomValue`, la variabile `randomValue` non รจ ancora inizializzata: viene lanciato un `ReferenceError`! Il motore non รจ andato giรน per la catena dell'ambito poichรฉ abbiamo dichiarato la variabile `randomValue` nella funzione `getInfo`.
</p>
</details>

---

###### 130. Qual รจ l'output?

```javascript
const myPromise = Promise.resolve('Woah some cool data');

(async () => {
  try {
    console.log(await myPromise);
  } catch {
    throw new Error(`Oops didn't work`);
  } finally {
    console.log('Oh finally!');
  }
})();
```

- A: `Woah some cool data`
- B: `Oh finally!`
- C: `Woah some cool data` `Oh finally!`
- D: `Oops didn't work` `Oh finally!`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Nel blocco `try`, stiamo loggando il valore atteso della variabile `myPromise`: `"Woah some cool data"`. Poichรฉ non sono stati generati errori nel blocco `try`, il codice nel blocco `catch` non viene eseguito. Il codice nel blocco `finally` viene eseguito _sempre_, `"Oh finally!"` viene loggato.

</p>
</details>

---

###### 131. Qual รจ l'output?

```javascript
const emojis = ['๐ฅ', ['โจ', 'โจ', ['๐', '๐']]];

console.log(emojis.flat(1));
```

- A: `['๐ฅ', ['โจ', 'โจ', ['๐', '๐']]]`
- B: `['๐ฅ', 'โจ', 'โจ', ['๐', '๐']]`
- C: `['๐ฅ', ['โจ', 'โจ', '๐', '๐']]`
- D: `['๐ฅ', 'โจ', 'โจ', '๐', '๐']`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Con il metodo `flat`, possiamo creare un nuovo array appiattito. La profonditร? dell'array appiattito dipende dal valore che passiamo. In questo caso, abbiamo passato il valore `1` (cosa che non dovevamo fare, questo รจ il valore predefinito), il che significa che solo gli array sulla prima profonditร? verranno concatenati. `['๐ฅ']` e `['โจ', 'โจ', ['๐', '๐']]` in questo caso. Concatenando questi due array si ottengono `['๐ฅ', 'โจ', 'โจ', ['๐', '๐']]`.
</p>
</details>

---

###### 132. Qual รจ l'output?

```javascript
class Counter {
  constructor() {
    this.count = 0;
  }

  increment() {
    this.count++;
  }
}

const counterOne = new Counter();
counterOne.increment();
counterOne.increment();

const counterTwo = counterOne;
counterTwo.increment();

console.log(counterOne.count);
```

- A: `0`
- B: `1`
- C: `2`
- D: `3`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

`counterOne` รจ un'istanza della classe `Counter`. La classe counter contiene una proprietร? `count` sul suo costruttore e un metodo `increment`. Per prima cosa, abbiamo invocato il metodo `increment` due volte chiamando `counterOne.increment()`. Attualmente, `counterOne.count` รจ `2`.

<img src="https://i.imgur.com/KxLlTm9.png" width="400">

Quindi, creiamo una nuova variabile `counterTwo` e la impostiamo uguale a `counterOne`. Poichรฉ gli oggetti interagiscono per riferimento, stiamo semplicemente creando un nuovo riferimento allo stesso punto della memoria a cui punta `counterOne`. Poichรฉ ha lo stesso punto in memoria, qualsiasi modifica apportata all'oggetto a cui fa riferimento `counterTwo`, si applica anche a `counterOne`. Attualmente, `counterTwo.count` รจ `2`.

Invochiamo `counterTwo.increment()`, che imposta `count` su `3`. Quindi, logghiamo il conteggio su `counterOne`, che stampa `3`.

<img src="https://i.imgur.com/BNBHXmc.png" width="400">

</p>
</details>

---

###### 133. Qual รจ l'output?

```javascript
const myPromise = Promise.resolve(Promise.resolve('Promise'));

function funcOne() {
  setTimeout(() => console.log('Timeout 1!'), 0);
  myPromise.then(res => res).then(res => console.log(`${res} 1!`));
  console.log('Last line 1!');
}

async function funcTwo() {
  const res = await myPromise;
  console.log(`${res} 2!`)
  setTimeout(() => console.log('Timeout 2!'), 0);
  console.log('Last line 2!');
}

funcOne();
funcTwo();
```

- A: `Promise 1! Last line 1! Promise 2! Last line 2! Timeout 1! Timeout 2!`
- B: `Last line 1! Timeout 1! Promise 1! Last line 2! Promise2! Timeout 2! `
- C: `Last line 1! Promise 2! Last line 2! Promise 1! Timeout 1! Timeout 2!`
- D: `Timeout 1! Promise 1! Last line 1! Promise 2! Timeout 2! Last line 2!`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Innanzitutto, invochiamo `funcOne`. Sulla prima riga di `funcOne`, chiamiamo la funzione _asincrona_ `setTimeout`, da cui la callback viene inviato all'API Web. (vedi l'articolo sul ciclo degli eventi [qui](https://dev.to/lydiahallie/javascript-visualized-event-loop-3dif))

Quindi chiamiamo la promise `myPromise`, che รจ un'operazione _asincrona_.

Sia la promise che il timeout sono operazioni asincrone, la funzione continua a funzionare mentre รจ impegnata a completare la promise e a gestire la callback `setTimeout`. Ciรฒ significa che `Last line 1!` viene registrato per primo, poichรฉ questa non รจ un'operazione asincrona.

Poichรฉ la callstack non รจ ancora vuota, la funzione `setTimeout` e la promise in `funcOne` non possono ancora essere aggiunte al callstack.

In `funcTwo`, la variabile `res` ottiene `Promise` perchรฉ `Promise.resolve(Promise.resolve('Promise'))` รจ equivalente a `Promise.resolve('Promise')` poichรฉ risolvere una promise risolve il suo valore. L'"attesa" in questa riga interrompe l'esecuzione della funzione fino a quando non riceve la risoluzione della promise e quindi continua a funzionare in modo sincrono fino al completamento, quindi `Promise 2!` e poi `Last line 2!` vengono registrati e `setTimeout` viene inviato all'API Web.

Quindi lo stack di chiamate รจ vuoto. Le promise sono _microattivitร?_, quindi vengono risolte per prime quando lo stack di chiamate รจ vuoto, quindi `Promise 1!` viene registrato.

Ora, da quando `funcTwo` รจ uscito dallo stack delle chiamate, lo stack delle chiamate รจ vuoto. Le callback in attesa nella coda (`() => console.log("Timeout 1!")` da `funcOne`, e `() => console.log("Timeout 2!")` da `funcTwo`) vengono aggiunti allo stack di chiamate uno per uno. Il primo callback registra `Timeout 1!` e viene eliminato dallo stack. Quindi, il secondo callback registra `Timeout 2!` e viene eliminato dallo stack.
</p>
</details>

---

###### 134. Come possiamo invocare `sum` in `sum.js` da `index.js?`

```javascript
// sum.js
export default function sum(x) {
  return x + x;
}

// index.js
import * as sum from './sum';
```

- A: `sum(4)`
- B: `sum.sum(4)`
- C: `sum.default(4)`
- D: I valori predefiniti non vengono importati con `*`, solo esportazioni nominali

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Con l'asterisco `*`, importiamo tutti i valori esportati da quel file, sia predefinito che nominale. Se avessimo il seguente file:

```javascript
// info.js
export const name = 'Lydia';
export const age = 21;
export default 'I love JavaScript';

// index.js
import * as info from './info';
console.log(info);
```

Verrebbe loggato quanto segue:

```javascript
{
  default: "I love JavaScript",
  name: "Lydia",
  age: 21
}
```

Per l'esempio `sum`, significa che il valore importato `sum` รจ simile a quanto segue:

```javascript
{ default: function sum(x) { return x + x } }
```

Possiamo invocare questa funzione, chiamando `sum.default`

</p>
</details>

---

###### 135. Qual รจ l'output?

```javascript
const handler = {
  set: () => console.log('Added a new property!'),
  get: () => console.log('Accessed a property!'),
};

const person = new Proxy({}, handler);

person.name = 'Lydia';
person.name;
```

- A: `Added a new property!`
- B: `Accessed a property!`
- C: `Added a new property!` `Accessed a property!`
- D: Nulla viene loggato

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Con un oggetto Proxy, possiamo aggiungere un comportamento personalizzato a un oggetto che gli passiamo come secondo argomento. In questo caso, passiamo all'oggetto `handler` che conteneva due proprietร?: `set` e `get`. `set` viene invocato ogni volta che _settiamo_ valori di proprietร?, `get` viene invocato ogni volta che _otteniamo_ (accediamo) valori di proprietร?.

Il primo argomento รจ un oggetto vuoto `{}`, che รจ il valore di `person`. A questo oggetto viene aggiunto il comportamento personalizzato specificato nell'oggetto `handler`. Se aggiungiamo una proprietร? all'oggetto `person`, `set` verrร? invocato. Se accediamo a una proprietร? sull'oggetto `person`, `get` viene invocato.

Innanzitutto, abbiamo aggiunto una nuova proprietร? `name` all'oggetto proxy (`person.name = "Lydia"`). `set` viene invocato e registra `"Added a new property!"`.

Quindi, accediamo a un valore di proprietร? sull'oggetto proxy, la proprietร? `get` sull'oggetto handler รจ stata invocata. `"Accessed a property!"` viene registrato.

</p>
</details>

---

###### 136. Quale delle seguenti opzioni modificherร? l'oggetto `persona`?

```javascript
const person = { name: 'Lydia Hallie' };

Object.seal(person);
```

- A: `person.name = "Evan Bacon"`
- B: `person.age = 21`
- C: `delete person.name`
- D: `Object.assign(person, { age: 21 })`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Con `Object.seal` possiamo impedire che nuove proprietร? vengano _aggiunte_ o che proprietร? esistenti vengano _rimosse_.

Tuttavia, puoi comunque modificare il valore delle proprietร? esistenti.

</p>
</details>

---

###### 137. Quale delle seguenti opzioni modificherร? l'oggetto `person`?

```javascript
const person = {
  name: 'Lydia Hallie',
  address: {
    street: '100 Main St',
  },
};

Object.freeze(person);
```

- A: `person.name = "Evan Bacon"`
- B: `delete person.address`
- C: `person.address.street = "101 Main St"`
- D: `person.pet = { name: "Mara" }`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Il metodo `Object.freeze` _congela_ un oggetto. Nessuna proprietร? puรฒ essere aggiunta, modificata o rimossa.

Tuttavia, blocca solo _poco profondamente_ l'oggetto, il che significa che solo le proprietร? _direct_ sull'oggetto sono bloccate. Se la proprietร? รจ un altro oggetto, come `address` in questo caso, le proprietร? su quell'oggetto non vengono bloccate e possono essere modificate.

</p>
</details>

---

###### 138. Qual รจ l'output?

```javascript
const add = x => x + x;

function myFunc(num = 2, value = add(num)) {
  console.log(num, value);
}

myFunc();
myFunc(3);
```

- A: `2` `4` and `3` `6`
- B: `2` `NaN` and `3` `NaN`
- C: `2` `Error` and `3` `6`
- D: `2` `4` and `3` `Error`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Per prima cosa, abbiamo invocato `myFunc()` senza passare alcun argomento. Dal momento che non abbiamo passato argomenti, `num` e `value` hanno i loro valori predefiniti: num รจ `2` e `value` il valore restituito dalla funzione `add`. Alla funzione `add`, passiamo `num` come argomento, che aveva il valore di `2`. `add` restituisce `4`, che รจ il valore di `value`.

Quindi, abbiamo invocato `myFunc(3)` e passato il valore `3` come valore per l'argomento `num`. Non abbiamo passato un argomento per `value`. 
Poichรฉ non abbiamo passato un valore per l'argomento `value`, ha ottenuto il valore predefinito: il valore restituito dalla funzione `add`. Ad `add` passiamo `num`, che ha il valore di `3`. `add` restituisce `6`, che รจ il valore di `value`.

</p>
</details>

---

###### 139. Qual รจ l'output?

```javascript
class Counter {
  #number = 10

  increment() {
    this.#number++
  }

  getNum() {
    return this.#number
  }
}

const counter = new Counter()
counter.increment()

console.log(counter.#number)
```

- A: `10`
- B: `11`
- C: `undefined`
- D: `SyntaxError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

In ES2020, possiamo aggiungere variabili private nelle classi usando `#`. Non possiamo accedere a queste variabili al di fuori della classe. Quando proviamo a registrare `counter.#number`, viene generato un SyntaxError: non possiamo accedervi al di fuori della classe `Counter`!

</p>
</details>

---

###### 140. Cosa manca?

```javascript
const teams = [
  { name: 'Team 1', members: ['Paul', 'Lisa'] },
  { name: 'Team 2', members: ['Laura', 'Tim'] },
];

function* getMembers(members) {
  for (let i = 0; i < members.length; i++) {
    yield members[i];
  }
}

function* getTeams(teams) {
  for (let i = 0; i < teams.length; i++) {
    // โจ SOMETHING IS MISSING HERE โจ
  }
}

const obj = getTeams(teams);
obj.next(); // { value: "Paul", done: false }
obj.next(); // { value: "Lisa", done: false }
```

- A: `yield getMembers(teams[i].members)`
- B: `yield* getMembers(teams[i].members)`
- C: `return getMembers(teams[i].members)`
- D: `return yield getMembers(teams[i].members)`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Per scorrere i `members` in ogni elemento dell'array `teams`, dobbiamo passare `teams[i].members` alla funzione `getMembers`. La funzione restituisce un oggetto. Per scorrere ogni elemento in questo oggetto generatore, dobbiamo usare `yield*`.

Se avessimo scritto `yield`, `return yield` o `return`, l'intera funzione del generatore sarebbe stata restituita la prima volta che abbiamo chiamato il metodo `next`.

</p>
</details>

---

###### 141. Qual รจ l'output?

```javascript
const person = {
  name: 'Lydia Hallie',
  hobbies: ['coding'],
};

function addHobby(hobby, hobbies = person.hobbies) {
  hobbies.push(hobby);
  return hobbies;
}

addHobby('running', []);
addHobby('dancing');
addHobby('baking', person.hobbies);

console.log(person.hobbies);
```

- A: `["coding"]`
- B: `["coding", "dancing"]`
- C: `["coding", "dancing", "baking"]`
- D: `["coding", "running", "dancing", "baking"]`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

La funzione `addHobby` riceve due argomenti, `hobby` e `hobby` con il valore predefinito dell'array `hobbies` sull'oggetto `person`.

Per prima cosa, invochiamo la funzione `addHobby` e passiamo `"running"` come valore per `hobby` e un array vuoto come valore per `hobby`. Poichรฉ passiamo un array vuoto come valore per `hobby`, `"running"` viene aggiunto a questo array vuoto.

Quindi, invochiamo la funzione `addHobby` e passiamo a `"dancing"` come valore per `hobby`. Non abbiamo passato un valore per `hobbies`, quindi ottiene il valore predefinito, la proprietร? `hobbies` sull'oggetto `person`. Spostiamo l'hobby `dancing` nell'array `person.hobbies`.

Infine, invochiamo la funzione `addHobby` e passiamo `"baking"` come valore per `hobby`, e l'array `person.hobbies` come valore per `hobby`. Spostiamo l'hobby `baking` nell'array `person.hobbies`.

Dopo aver fatto un push di `dancing` e `baking`, il valore di `person.hobbies` รจ `["coding", "dancing", "baking"]`

</p>
</details>

---

###### 142. Qual รจ l'output?

```javascript
class Bird {
  constructor() {
    console.log("I'm a bird. ๐ฆข");
  }
}

class Flamingo extends Bird {
  constructor() {
    console.log("I'm pink. ๐ธ");
    super();
  }
}

const pet = new Flamingo();
```

- A: `I'm pink. ๐ธ`
- B: `I'm pink. ๐ธ` `I'm a bird. ๐ฆข`
- C: `I'm a bird. ๐ฆข` `I'm pink. ๐ธ`
- D: Niente, non abbiamo chiamato alcun metodo

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Creiamo la variabile `pet` che รจ un'istanza della classe `Flamingo`. Quando istanziamo questa istanza, il `constructor` su `Flamingo` viene chiamato. Per prima cosa, `"I'm pink. ๐ธ"` viene loggato, dopodichรฉ chiamiamo `super()`. 

`super()` chiama il costruttore della classe genitore, `Bird`. Il costruttore in `Bird` viene chiamato e registra `"I'm a bird. ๐ฆข"`.

</p>
</details>

---

###### 143. Quale delle opzioni genera un errore?

```javascript
const emojis = ['๐', '๐๐ผ', '๐', 'โญ'];

/* 1 */ emojis.push('๐ฆ');
/* 2 */ emojis.splice(0, 2);
/* 3 */ emojis = [...emojis, '๐ฅ'];
/* 4 */ emojis.length = 0;
```

- A: 1
- B: 1 and 2
- C: 3 and 4
- D: 3

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

La chiave `const` significa che non possiamo _ridichiarare_ il valore di quella variabile, รจ di _sola lettura_. Tuttavia, il valore stesso non รจ immutabile. Le proprietร? dell'array `emojis` possono essere modificate, ad esempio facendo un push di nuovi valori, collegandoli o impostando la lunghezza dell'array su 0.

</p>
</details>

---

###### 144. Cosa dobbiamo aggiungere all'oggetto `person` per ottenere `["Lydia Hallie", 21]` come output di `[...person]`?

```javascript
const person = {
  name: "Lydia Hallie",
  age: 21
}

[...person] // ["Lydia Hallie", 21]
```

- A: Nulla, gli oggetti sono iterabili di default
- B: `*[Symbol.iterator]() { for (let x in this) yield* this[x] }`
- C: `*[Symbol.iterator]() { yield* Object.values(this) }`
- D: `*[Symbol.iterator]() { for (let x in this) yield this }`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Gli oggetti non sono iterabili per impostazione predefinita. Un iterabile รจ un iterabile se รจ presente il protocollo iteratore. 
Possiamo aggiungerlo manualmente aggiungendo il simbolo dell'iteratore `[Symbol.iterator]`, che deve restituire un oggetto generatore, ad esempio trasformandolo in una funzione del generatore `*[Symbol.iterator]() {}`. Questa funzione di generazione deve fornire gli `Object.values` dell'oggetto `person` se vogliamo che restituisca l'array `["Lydia Hallie", 21]`: `yield* Object.values(this)`.

</p>
</details>

---

###### 145. Qual รจ l'output?

```javascript
let count = 0;
const nums = [0, 1, 2, 3];

nums.forEach(num => {
	if (num) count += 1
})

console.log(count)
```

- A: 1
- B: 2
- C: 3
- D: 4

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

La condizione `if` all'interno del ciclo `forEach` controlla se il valore di `num` รจ veritiero o falso. Poichรฉ il primo numero nell'array `nums` รจ `0`, ovvero un valore falso, il blocco di codice dell'istruzione `if` non verrร? eseguito. `count` viene incrementato solo per gli altri 3 numeri nell'array `nums`, `1`, `2` e `3`. Poichรฉ `count` viene incrementato di `1` 3 volte, il valore di `count` รจ `3`.

</p>
</details>

---

###### 146. Qual รจ l'output?

```javascript
function getFruit(fruits) {
	console.log(fruits?.[1]?.[1])
}

getFruit([['๐', '๐'], ['๐']])
getFruit()
getFruit([['๐'], ['๐', '๐']])
```

- A: `null`, `undefined`, ๐
- B: `[]`, `null`, ๐
- C: `[]`, `[]`, ๐
- D: `undefined`, `undefined`, ๐

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

Il `?` ci consente di accedere opzionalmente a proprietร? nidificate piรน profonde all'interno degli oggetti. Stiamo cercando di registrare l'elemento sull'indice `1` all'interno del sottoarray che si trova sull'indice `1` dell'array `fruits`. Se il sottoarray sull'indice `1` nell'array `fruits` non esiste, restituirร? semplicemente `undefined`. Se il sottoarray sull'indice `1` nell'array `fruits` esiste, ma questo sottoarray non ha un elemento nel suo indice `1`, restituirร? comunque `undefined`.

Innanzitutto, stiamo cercando di registrare il secondo elemento nel sottoarray `['๐']` di `[['๐', '๐'], ['๐']]`. Questo sottoarray contiene solo un elemento, il che significa che non c'รจ alcun elemento nell'indice `1`, e restituisce `undefined`.

Quindi, stiamo invocando la funzione `getFruits` senza passare un valore come argomento, il che significa che `fruits` ha un valore di `undefined` per impostazione predefinita. Poichรฉ stiamo concatenando condizionatamente l'elemento sull'indice `1` di `fruits`, restituisce `undefined` poichรฉ questo elemento sull'indice `1` non esiste.

Infine, stiamo cercando di registrare il secondo elemento nel sottoarray `['๐', '๐']` di `['๐'], ['๐', '๐']`. L'elemento nell'indice `1` all'interno di questo sottoarray รจ `๐`, che viene registrato.
</p>
</details>

---

###### 147. Qual รจ l'output?

```javascript
class Calc {
	constructor() {
		this.count = 0 
	}

	increase() {
		this.count ++
	}
}

const calc = new Calc()
new Calc().increase()

console.log(calc.count)
```

- A: `0`
- B: `1`
- C: `undefined`
- D: `ReferenceError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

Impostiamo la variabile `calc` uguale a una nuova istanza della classe `Calc`. Quindi, istanziamo una nuova `Calc` e invochiamo il metodo `increase` su questa istanza. Poichรฉ la proprietร? count รจ all'interno del costruttore della classe `Calc`, la proprietร? count non รจ condivisa sul prototipo di `Calc`. Ciรฒ significa che il valore di count non รจ stato aggiornato per l'istanza a cui punta il calc, count รจ ancora `0`.
</p>
</details>

---

###### 148. Qual รจ l'output?

```javascript
const user = {
	email: "e@mail.com",
	password: "12345"
}

const updateUser = ({ email, password }) => {
	if (email) {
		Object.assign(user, { email })
	}

	if (password) {
		user.password = password
	}

	return user
}

const updatedUser = updateUser({ email: "new@email.com" })

console.log(updatedUser === user)
```

- A: `false`
- B: `true`
- C: `TypeError`
- D: `ReferenceError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

La funzione `updateUser` aggiorna i valori delle proprietร? `email` e `password` sull'utente se i loro valori vengono passati alla funzione, dopodichรฉ la funzione restituisce l'oggetto `user`. Il valore restituito dalla funzione `updateUser` รจ l'oggetto `user`, il che significa che il valore di `updateUser` รจ un riferimento allo stesso oggetto `user` a cui punta `user`. `updatedUser === user` รจ uguale a `true`.

</p>
</details>

---

###### 149. Qual รจ l'output?

```javascript
const fruit = ['๐', '๐', '๐']

fruit.slice(0, 1)
fruit.splice(0, 1)
fruit.unshift('๐')

console.log(fruit)
```

- A: `['๐', '๐', '๐']`
- B: `['๐', '๐']`
- C: `['๐', '๐', '๐']`
- D: `['๐', '๐', '๐', '๐']`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Per prima cosa, invochiamo il metodo `slice` sull'array fruit. Il metodo slice non modifica l'array originale, ma restituisce il valore che ha tagliato fuori dall'array: l'emoji banana.
Quindi, invochiamo il metodo `splice` sull'array fruit. Il metodo splice modifica l'array originale, il che significa che l'array fruit ora รจ composto da `['๐', '๐']`.
Infine, invochiamo il metodo `unshift` sull'array `fruit`, che modifica l'array originale aggiungendo il valore fornito, '๐' in questo caso, come primo elemento nell'array. L'array fruit ora รจ composto da `['๐', '๐', '๐']`.

</p>
</details>

---

###### 150. Qual รจ l'output?

```javascript
const animals = {};
let dog = { emoji: '๐ถ' }
let cat = { emoji: '๐' }

animals[dog] = { ...dog, name: "Mara" }
animals[cat] = { ...cat, name: "Sara" }

console.log(animals[dog])
```

- A: `{ emoji: "๐ถ", name: "Mara" }`
- B: `{ emoji: "๐", name: "Sara" }`
- C: `undefined`
- D: `ReferenceError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

Le chiavi degli oggetti vengono convertite in stringhe.

Poichรฉ il valore di `dog` รจ un oggetto, `animals[dog]` significa in realtร? che stiamo creando una nuova proprietร? chiamata `"object Object"` uguale al nuovo oggetto. 
`animals["object Object"]` รจ ora uguale a `{ emoji: "๐ถ", name: "Mara"}`.

Anche `cat` รจ un oggetto, il che significa che `animals[cat]` in realtร? stiamo sovrascrivendo il valore di `animals["object Object"]` con le nuove proprietร? cat.

Loggando `animals[dog]`, o effettivamente `animals["object Object"]`, poichรฉ la conversione dell'oggetto `dog` in una stringa risulta `"object Object"`, restituisce  `{ emoji: "๐", name: "Sara" }`.

</p>
</details>

---

###### 151. Qual รจ l'output?

```javascript
const user = {
	email: "my@email.com",
	updateEmail: email => {
		this.email = email
	}
}

user.updateEmail("new@email.com")
console.log(user.email)
```

- A: `my@email.com`
- B: `new@email.com`
- C: `undefined`
- D: `ReferenceError`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: A

La funzione `updateEmail` รจ una arrow function e non รจ legata all'oggetto `user`. Ciรฒ significa che la parola chiave `this` non si riferisce all'oggetto `user`, ma in questo caso si riferisce allo scope globale. Il valore di `email` all'interno dell'oggetto `user` non viene aggiornato. Quando si stampa il valore di `user.email`, viene restituito il valore originale ovvero `my@email.com`.

</p>
</details>

---

###### 152. Qual รจ l'output?

```javascript
const promise1 = Promise.resolve('First')
const promise2 = Promise.resolve('Second')
const promise3 = Promise.reject('Third')
const promise4 = Promise.resolve('Fourth')

const runPromises = async () => {
	const res1 = await Promise.all([promise1, promise2])
	const res2  = await Promise.all([promise3, promise4])
	return [res1, res2]
}

runPromises()
	.then(res => console.log(res))
	.catch(err => console.log(err))
```

- A: `[['First', 'Second'], ['Fourth']]`
- B: `[['First', 'Second'], ['Third', 'Fourth']]`
- C: `[['First', 'Second']]`
- D: `'Third'`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: D

Il metodo `Promise.all` esegue le promise passate in parallelo. Se una promise fallisce, il metodo `Promise.all` effettua un _rejects_ con il valore della promise rifiutata. In questo caso, `promise3` ha rifiutato con il valore `"Third"`. Stiamo rilevando il valore rifiutato nel metodo `catch` concatenato sulla chiamata `runPromises` per rilevare eventuali errori all'interno della funzione `runPromises`. Solo `"Third"` viene registrato, poichรฉ `promise3` viene rifiutato con questo valore.

</p>
</details>

---

###### 153. Quale dovrebbe essere il valore di `method` per loggare ` {nome: "Lydia", etร?: 22} `?

```javascript
const keys = ["name", "age"]
const values = ["Lydia", 22]

const method = /* ?? */
Object[method](keys.map((_, i) => {
	return [keys[i], values[i]]
})) // { name: "Lydia", age: 22 }
```

- A: `entries`
- B: `values`
- C: `fromEntries`
- D: `forEach`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Il metodo `fromEntries` trasforma un array 2d in un oggetto. Il primo elemento in ogni sottoarray sarร? la chiave e il secondo elemento in ogni sottoarray sarร? il valore. In questo caso, stiamo mappando sull'array `keys`, che restituisce un array il cui primo elemento รจ l'elemento nell'array di chiavi sull'indice corrente e il secondo elemento รจ l'elemento dell'array di valori sull'indice corrente.

Questo crea una matrice di sottoarray contenenti le chiavi e i valori corretti, che risulta in `{ nome: "Lydia", etร?: 22 }`

</p>
</details>

---

###### 154. Qual รจ l'output?

```javascript
const createMember = ({ email, address = {}}) => {
	const validEmail = /.+\@.+\..+/.test(email)
	if (!validEmail) throw new Error("Valid email pls")

	return {
		email,
		address: address ? address : null
	}
}

const member = createMember({ email: "my@email.com" })
console.log(member)
```

- A: `{ email: "my@email.com", address: null }`
- B: `{ email: "my@email.com" }`
- C: `{ email: "my@email.com", address: {} }`
- D: `{ email: "my@email.com", address: undefined }`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: C

Il valore predefinito di `address` รจ un oggetto vuoto `{}`. Quando abbiamo impostato la variabile `member` uguale all'oggetto restituito dalla funzione `createMember`, non abbiamo passato un valore per `address`, il che significa che il valore di `address` รจ l'oggetto vuoto predefinito `{}`. Un oggetto vuoto รจ un valore veritiero, il che significa che la condizione `address ? address : null` restituisce `true`. Il valore di `address` รจ l'oggetto vuoto `{}`.

</p>
</details>

---

###### 155. Qual รจ l'output?

```javascript
let randomValue = { name: "Lydia" }
randomValue = 23

if (!typeof randomValue === "string") {
	console.log("It's not a string!")
} else {
	console.log("Yay it's a string!")
}
```

- A: `It's not a string!`
- B: `Yay it's a string!`
- C: `TypeError`
- D: `undefined`

<details><summary><b>Risposta</b></summary>
<p>

#### Risposta: B

La condizione all'interno dell'istruzione `if` controlla se il valore di `!typeof randomValue` รจ uguale a `"string"`. L'operatore `!` converte il valore in un valore booleano. Se il valore รจ vero, il valore restituito sarร? `false`, se il valore รจ falso, il valore restituito sarร? `true`. In questo caso, il valore restituito di `typeof randomValue` รจ il vero valore `"number"`, il che significa che il valore di `!typeof randomValue` รจ il valore booleano `false`.

`!typeof randomValue === "string"` restituisce sempre false, poichรฉ stiamo effettivamente controllando `false === "string"`. Poichรฉ la condizione ha restituito `false`, il blocco di codice dell'istruzione `else` viene eseguito e `Yay it's a string!` viene registrato.

</p>
</details>
