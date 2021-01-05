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

Nel nostro caso vogliamo generare una serie di oggetti in una sequenza temporizzata \(es.: generare dieci frecce una alla volta\)



