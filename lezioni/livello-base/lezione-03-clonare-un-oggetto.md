---
description: >-
  In questa lezione impareremo a creare un oggetto in scena partendo da un
  prefab.
---

# Lezione 03 - Clonare un Oggetto

Per poter creare un oggetto in scena a partire da un prefab, si può utilizzare il metodo _Instantiate_. 

{% hint style="info" %}
Per questa lezione, si consiglia di utilizzare la scena **Lezione 03 - Clonare un Oggetto** inclusa [nel progetto di supporto](https://github.com/thebitcave/gitbook-guida-bolt/releases).
{% endhint %}

### Aprire la Scena

Una volta aperta la scena di supporto, sarà possibile visualizzare un oggetto _Spawner_:

* Selezioniamo il gameobject _Spawner_ e notiamo che è già presente il componente _Flow Machine_.
* Apriamo il grafo cliccando su _Edit Graph_ nell'Inspector
* Eliminiamo il nodo _Start_ perché non ci servirà

### L'Evento Update

Durante l'evento Update andremo a controllare se il giocatore ha premuto un tasto della tastiera e, in caso positivo, andremo a creare un oggetto.



