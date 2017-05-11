# Le Chiusure

#### Ovvero dove si comprende che se una porta è chiusa si può passare dalla finestra 🚪
<hr>

<sup>[(MDN)][Object]</sup>.

Il concetto di **closures** è strettamente legato alla portata delle variabili. È un concetto semplice, che si spiega ancora più facilmente con un esempio.

```javascript
var gatto = { nome : 'Dorakiki' };

function nomeGatto() {
	console.log(gatto.nome);
}

nomeGatto(); // Giuliano

```

la variabile `gatto` è dichiarata al di fuori della funzione `nomeGatto` ma questo non impedisce a quest'ultima di accedervi. 

In javascript le variabili dichiarate nello *scope* di una funzione sono accessibili da tutte le funzioni create nello stesso spazio.

Una **chiusura** è dunque una funzione che utilizza le variabili definite nello spazio nel quale è stata creata.

Per prima cosa cosa creiamo una funzione `creaCroccantini()`. Al suo interno definiamo una variabile `croccantini`, inizialmente uguale a `0`.

All'interno di questa prima funzione ne creiamo un'altra, la chiamiamo `aggiungiUnCroccantino()`. Il suo scopo è solo di aggiungere una unità a `croccantini`, variabile a cui ha accesso grazie al fatto di essere creata nello stesso *scope*. 
 

```javascript
function creaCroccantini() {

	var croccantini = 0;
	
	function aggiungiUnCroccantino() {
	
		croccantini++;
		console.log(croccantini);
	
	}

	return aggiungiUnCroccantino;
}

```

`creaCroccantini()` restituisce la funzione `aggiungiUnCroccantino()` in questo modo possiamo eseguirla quando serve. Ed è quello che facciamo qui in basso. Assegniamo una nuova variabile `dammiUnCroccantino` al valore restituito da `creaCroccantini()` che è la funzione `aggiungiUnCroccantino()`.


```javascript
var dammiUnCroccantino = creaCroccantini();

```

`dammiUnCroccantino` è una **chiusura**, essa ha accesso alla variabile `croccantini` anche se la funzione `creaCroccantini()` è già stata eseguita da un bel pezzo. So che può sembrare non intuitivo, in fin dei conti quella variabile era stata creata altrove, ma queste sono le magie di javascript. 

La **chiusura** ha la memoria lunga, e si ricorda, e utilizza tutte le variabili del suo *scope*.

La prova ?

```javascript
dammiUnCroccantino(); // 1
dammiUnCroccantino(); // 2
dammiUnCroccantino(); // 3
dammiUnCroccantino(); // 4
```



[Object]: (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)



[index]: ../index.md
[2]: ./proprieta_privata.md
