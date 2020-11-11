---
description: >-
  In questa lezione impareremo a muovere un oggetto tramite l'istruzione di
  traslazione di un Transform.
---

# Lezione 2 - Spostare un Oggetto

Esistono diverse possibilità nel caso si volesse spostare un oggetto in scena: una di queste è quella di traslarlo intervenendo sul suo _Transform_ \(in particolare, i valori di _position_\).

{% hint style="info" %}
Per questa lezione, si consiglia di utilizzare la scena **Lezione 02 - Spostare un Oggetto** inclusa [nel progetto di supporto](https://github.com/thebitcave/gitbook-guida-bolt/releases).
{% endhint %}

### L'Attributo Position

La posizione \(**position**\) di un oggetto è data da tre valori \(x, y, z\) che indicano, rispettivamente la posizione nello spazio rispetto alle direzioni _destra/sinistra_, _su/giù_, _avanti/indietro_. Per identificare una serie di valori di questo genere, si utilizza l'elemento [Vector3](https://docs.unity3d.com/ScriptReference/Vector3.html).

{% hint style="success" %}
Se volessi spostare verso l'alto un oggetto, dovrei sommare al valore _y_ della _position_ un numero positivo, ad esempio _\(0, 4, 0\)_ Se invece volessi spostarlo verso il basso, dovrei utilizzare un valore negativo, ad esempio _\(0, -6, 0\)_.
{% endhint %}

### Utilizzare il metodo Translate\(\)



