# Gli oggetti

<hr>

Caro Gatto, ora che sappiamo cosa è un oggetto, proviamo a crearne uno insieme. 

Esistono vari modi (patterns). Questi sono quelli più utilizzati.

##### con un Oggetto Letterale
```javascript
var gatto = {};
```

##### con il metodo Object.create();
```javascript
var gatto = Object.create(null);
```

##### con un Costruttore 

```javascript
// NB la lettera maiuscola è una convenzione importante!
var Gatto = function(nome) {

  this.vite = 9;
  this.nome = nome;
}
var gatto = new Gatto("Dorakiki"); 

```

##### con un Costruttore + Prototipo

```javascript
function Gatto(){};
Gatto.prototype.nome = "Dorakiki";
var gatto = new Gatto(); 

```

Se sei curioso di saperere cosa fa l'operatore **new** <sup>[(MDN)][new]</sup> sappi che new usa un suo metodo "Constructor" e che:

1. Crea un nuovo oggetto che eredita da Gatto.prototype
2. Esegue la funzione Gatto assegnando `this` al nuovo oggetto (e passando dei parametri, se ci sono, ad esempio il nome 'Dorakiki')
3. Restituisce l'oggetto al punto 1

##### con la sintassi ES6 

```javascript
class Gatto  {
  constructor(nome) {
    this.nome = nome;
    this.vite = 9;
  }
}
var gatto = new Gatto("Dorakiki"); 

```


Practical Patterns for Creating Objects

Constructor Pattern for Creating Objects

Prototype Pattern for Creating Objects

Accessing and Enumerating Properties on Objects

Deleting Properties of an Object 
[new]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new
