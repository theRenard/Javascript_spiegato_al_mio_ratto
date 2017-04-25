# Gli oggetti

#### Ovvero, che diamine è un oggetto?
<hr>

Caro gatto, Javascript è un linguaggio ad oggetti, gli oggetti li userai spesso, sempre. Questo corso inizia facile, spiegando cosa è un oggetto <sup>[(MDN)][Object]</sup>.

Un oggetto è una collezione non ordinata di dati (proprietà) e funzioni (metodi) definiti come coppie nome **nome** e **valore**. 

```javascript
{ nome: 'valore' };  // eccomi, sono un oggetto.
```

Per farla semplice, facciamo che tu sei un oggetto. Non è bello da dire, sei un animale, ma facciamo che per descriverti usiamo un oggetto, e per comodità assegnamo a questo oggetto una variabile `gatto`.

```javascript
var gatto = {};
```
Ora, come tutti i gatti hai nove vite, e senza dubbio la capacità di perderne una a settimana. Una proprietà e un metodo che potremmo aggiungere all'oggetto che ti descrive. 

```javascript
var gatto = {

	// una proprietà
	vite: 9,

	// un metodo
	muore: function() {
		// this in questo caso è l'oggetto stesso, è
		// come se scrivessimo gatto.vite;
		// ma parleremo di this più in là
		this.vite -= 1;
	}	
}

```

Per accedere ai tuoi metodi e alle tue proprietà, (**get**) puoi utilizzare il punto o la parentesi quadra.

```javascript
// con il punto, detto anche dot notation
console.log( gatto.vite ); // 9

gatto.muore();  // avvelenato ?

// con le parentesi quadre, o bracket notation
console.log( gatto['vite'] ); // 8

```
E con lo stesso sistema caro Gatto, puoi aggiungere nuove proprietà e nuovi metodi (**set**). 

```javascript
// ecco una nuova proprietà
gatto.nome = 'Dorakiki';

// un nuovo valore a un proprietà esistente
gatto.vite = 5;

// e un nuovo medoto
gatto['rivive'] = function() {
	this.vite += 1; // molto utile.
}

```

La *dot notation* è probabilmente più semplice da leggere, ma con le parentesi quadre puoi usare una variabile per recuperare un valore, cosa piuttosto pratica.

```javascript
// carino no?
gatto.proprieta_1.sotto_proprieta_2.metodo().valore;
	
// 
var valoreDinamico = 'nome';
gatto[valoreDinamico] = 'Dorakiki';
```

Tutto chiaro fin qui ? Passiamo alla parte 2, ovvero "[Una ricca eredità][2]".


[Object]: (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)

[index]: ../index.md
[2]: ./una_ricca_eredita.md
