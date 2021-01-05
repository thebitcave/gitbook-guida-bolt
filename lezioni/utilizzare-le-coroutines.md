---
description: >-
  In questa lezione andremo ad scoprire come utilizzare un Custom Event in
  modalità Coroutine.
---

# Lezione 04 - Utilizzare le Coroutines

In Unity, ma anche nella programmazione in generale, una [Coroutine ](https://docs.unity3d.com/Manual/Coroutines.html)è una funzione che può essere messa in pausa e riattivata all'avverarsi di alcuni particolari eventi \(es.: al frame successivo, dopo un determinato periodo, etc.\).

{% hint style="info" %}
Per questa lezione, si consiglia di utilizzare la scena **Lezione 04 - Utilizzare le Coroutines** inclusa [nel progetto di supporto](https://github.com/thebitcave/gitbook-guida-bolt/releases).
{% endhint %}

### Aprire la Scena

Una volta aperta la scena di supporto, sarà possibile visualizzare un oggetto _Spawner_:

* Selezioniamo il gameobject _Spawner_ e notiamo che è già presente il componente _Flow Machine_.
* Apriamo il grafo cliccando su _Edit Graph_ nell'Inspector
* Noteremo che è presente un singolo evento _Update_ che intercetta la pressione del tasto _Space_

![Il grafo iniziale](../.gitbook/assets/grafo_iniziale.png)

### Creare un Evento Personalizzato

Un **Evento Personalizzato** \(**Custom Event**\) ci permette di creare un evento simile a quelli già presenti in Unity ma che potremo eseguire a nostro piacimento dallo stesso grafo o da grafi esterni.

{% hint style="info" %}
Per avere una panoramica di come è possibile utilizzare gli Eventi Personalizzati, aprire la scena **Esempio 01 - Eventi Personalizzati** nel progetto di supporto.
{% endhint %}

Un Evento Personalizzato è di solito formato da due entità:

* L'evento vero e proprio: che andrà ad eseguire i nodi contenuti
* L'attivatore dell'evento \(_trigger_\): che comanderà all'evento di eseguire il suo contenuto

Nel nostro caso vogliamo generare una serie di oggetti in una sequenza temporizzata \(es.: generare dieci frecce una alla volta\).

Cominciamo con il creare un Evento Personalizzato:

* Nel grafo dello Spawner, clicchiamo il pulsante destro in uno spazio vuoto e selezioniamo _Event &gt; Custom Event_
* Nel secondo campo \(quello con l'identificatore arancione\) inseriamo il nome dell'evento: _SpawnElements_
* In modo del tutto simile a quanto fatto nella _Lezione 03_, generiamo un prefab \(_Arrow_\) aggiungendo un nodo **Instantiate**, come mostrato nella seguente immagine:

![](../.gitbook/assets/evento_personalizzato.png)

### Attivare l'Evento

Al contrario degli eventi di Unity, un evento personalizzato deve essere lanciato all'interno del nostro codice tramite un attivatore \(**Trigger**\):

* Dall'uscita True del nodo Branch, clicchiamo e trasciniamo creando un nodo _Event &gt; Trigger Custom Event_
* Nel secondo campo \(quello con l'identificatore arancione\) inseriamo il nome dell'evento che vogliamo eseguire: _SpawnElements_

![](../.gitbook/assets/esecuzione_evento.png)

Provando ad eseguire l'applicazione, potremo notare che la freccia viene generata ogni volta che andremo a premere la barra spaziatrice.

Rispetto alla lezione precedente, abbiamo slegato l'esecuzione dei nodi che generano la freccia dal controllo dell'interazione con il giocatore.

### Generare Elementi Multipli

Torniamo al nostro evento personalizzato: la nostra intenzione è di generare una serie di frecce invece di una singola.

{% hint style="info" %}
Per poter eseguire un numero finito di volte una serie di istruzioni, una delle possibilità è quella di usare l'unità **For Loop**.
{% endhint %}

* Tra i nodi _Custom Event_ e _Instantiate_, inseriamo una unità For Loop, come mostrato nella figura seguente:

![Inserimento del ciclo For Loop](../.gitbook/assets/for_loop.png)

Notare che il pin di uscita utilizzato è **Body**: tutto ciò che segue verrà eseguito una volta per ogni ciclo \(nel nostro caso, 10 volte\).

Il nodo **Exit** ci permette di "proseguire" l'esecuzione di altro codice una volta finiti i cicli.

Provate ad eseguire l'applicazione: noterete che, ogni volta che viene premuta la barra spaziatrice, vengono generate 10 frecce contemporaneamente.

### Temporizzare l'Esecuzione delle Unità

I comandi vengono solitamente eseguiti immediatamente uno dopo l'altro e non è possibile "aspettare" del tempo prima di eseguire quello successivo. Per poter effettuare una operazione di questo tipo, è necessario ricorrere ad una [Coroutine](https://docs.unity3d.com/Manual/Coroutines.html) che non segue il regolare svolgersi dei comandi e può essere messa in pausa.

Dobbiamo prima di tutto trasformare il nostro evento personalizzato in una Coroutine:

* Selezioniamo il _Custom Event_ e, nel _Graph Inspector_, selezioniamo la spunta _Coroutine_
* Noteremo che nella unità apparirà una icona identificativa

![](../.gitbook/assets/coroutine.png)

Per temporizzare l'esecuzione dei comandi, aggiungiamo un ritardo:

* All'uscita del nodo _Instantiate_, aggiungiamo il nodo _Time &gt; Wait for Seconds_
* Nel campo Delay, inseriamo il valore _0.2_ \(secondi\)

Provate ad eseguire l'applicazione e vedrete che ora le frecce vengono generate una di seguito all'altra con un ritardo di 200 millisecondi

![](../.gitbook/assets/ritardo_spawn.png)

### Ultime Migliorie

Il sistema è funzionante, ma può essere migliorato con alcuni piccoli ritocchi.

#### Gestire il Numero di Oggetti Generati

Al momento il numero di elementi generati è fissato a 10: possiamo rendere più flessibile il nostro evento personalizzato tramite l'aggiunta di un parametro \(**Argument**\):

* Nel nodo _Custom Event_, sostituire inserire il valore _1_ nel campo _Arguments_
* Apparirà un pin in uscita di colore verde
* Collegare il pin \(che sarà il nostro parametro in ingresso\) con il valore _Last_ dell'unità _For Loop_

![](../.gitbook/assets/argument_in.png)

Il parametro in ingresso dovrà essere "passato" dal trigger:

* Nell'unità _Trigger Custom Event_ inseriamo il valore _1_ nel campo Arguments: comparirà un pin in ingresso
* Collegare il nuovo pin ad una unità _int Literal_
* Assegnare un valore maggiore di zero all'unità

![](../.gitbook/assets/trigger_arguments.png)

Una volta lanciata l'applicazione, sarà possibile notare che il numero di frecce generate è pari al valore passato.

#### Interrompere le Interazioni in fase di Esecuzione

Per come è strutturata l'applicazione, è possibile generare più serie di eventi sovrapposti \(ad esempio, premendo più volte la barra spaziatrice\). Per migliorare l'interazione, sarebbe meglio pensare di disattivare l'interazione con il giocatore fino a che il ciclo non abbia terminato di eseguire i comandi.

Per fare questo utilizzeremo una variabile booleana che indica se il ciclo è in esecuzione oppure no.

* Creiamo una _Graph Variable_ \(nel pannello _Variables_\) di tipo _bool_ e chiamata _canShoot_
* Assegnamole un valore di partenza _true_

![](../.gitbook/assets/variables%20%281%29.png)

* Trasciniamo la variabile appena creata nel grafo, vicino all'unità _Input.GetKeyDown_
* Colleghiamo le due unità tra loro con una unità _Logic &gt; And_
* Colleghiamo il pin di uscita di _And_ al pin di entrata del _Branch_

![](../.gitbook/assets/branch%20%281%29.png)

Lo schema appena creato ci permette di lanciare l'evento solo se è stata premuta la barra spaziatrice e la variabile _canShoot_ è vera. Vogliamo che la variabile diventi falsa durante l'esecuzione del ciclo.

* Spostiamoci nel evento personalizzato e tra il nodo _Custom Event_ e il _For Loop_ inseriamo una unità _Variable &gt; Graph &gt; Set Graph Variable_
* Impostiamo il nome della variabile a _canShoot_
* Assegnamo un _bool Literal_ al pin di ingresso con valore _false_

![](../.gitbook/assets/set_bool.png)

Appena prima di cominciare il ciclo, la variabile viene impostata ad un valore falso, impedendo così all'evento update di generare ulteriori eventi.

* Nel pin Exit dell'unità For Loop, inseriamo gli stessi elementi di sopra, ma il bool Literal dovrà essere true, in modo tale da riattivare la possibilità di sparare

![](../.gitbook/assets/set_bool_true.png)

Mandate in esecuzione l'applicazione e sarà possibile sparare solamente una volta terminato il ciclo di fuoco precedente.

