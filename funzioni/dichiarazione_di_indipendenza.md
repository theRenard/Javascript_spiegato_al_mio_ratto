# Come Funziona la Funzione

#### dove si scopre chi fa cosa 
<hr>

Passiamo oltre, parliamo di *dichiarazione* e di *espressione*, ma prima un esempio, guarda attentamente:

```javascript
// Esempio 1
function faiQualcosa() {
	// ... fai qualcosa
}

// Esempio 2
var faiQualcosa = function() {
	// ... fai qualcosa
};

```

La differenza è sottile, e in effetti queste due funzioni fanno la stessa cosa. 
Ma c'è un ma. 

L'esempio 1 è una **dichiarazione d'espressione**, l'esempio 2 è una **espressione di funzione**. 
Me ne rendo conto, vuol dire ben poco, ma ora ci arriviamo, lascia che prima ti spieghi cosa è l'**hoisting**.

Se il tuo codice si eseguisse proceduralmente, le tue funzioni dovrebbero essere dichiarate **prima** di essere utilizzate, altrimenti ci sarebbe un errore `not defined`.

1. Ti spiego nella funzione come fare qualcosa
2. Esegui la funzione

Guarda qui:

```javascript
diQualcosa(); // ciaone!

function diQualcosa() {
	console.log('ciaone!');
}

```

Eppure, strano a dirsi, il codice qui sopra funziona!

Succede perché Javascript è abbastanza gentile da prendere la tua *dichiarazione di funzione* e trascriverla all'inizio del contesto di esecuzione. In pratica la sposta in alto. 

Così:


```javascript
function diQualcosa() {
	console.log('ciaone!');
}

diQualcosa(); // ciaone!

```

Tornando all'esempio 2, la funzione è accessibile solo tramite la variabile `faiQualcosa`, in questo caso l'hoisting non avviene, e quindi, guarda un po' cosa succede se facciamo

```javascript
diQualcosa(); 

var diQualcosa = function() {
	console.log('ciaone!');
};

// diQualcosa is not a function

```



[Object]: (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)


[index]: ../index.md
