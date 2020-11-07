# Tipi e Variabili

### I Tipi

In Bolt, come in qualsiasi linguaggio di programmazione moderna, ogni elemento che andiamo a "sfruttare" deve essere di una determinata tipologia e questa tipologia deve essere dichiarata in qualche modo. Unity3D, tramite Bolt, non fa eccezione \(mi serve un Collider oppure un Roigidbody?\).

Per differenziare gli elementi utilizzati, si ricorre alla definizione di **Tipo** \(in inglese **Type**\). In Unity esistono centinaia di tipi \(potete crearne anche di vostri!\) e Bolt, per individuarli, ricorre ad icone identificative.

Di seguito sono elencati alcuni dei tipi che andrete ad utilizzare più spesso:

| Tipo | Descrizione |
| :--- | :--- |
| `Float` | Rappresenta un numero decimale \(ad esempio 0.4 oppure 20.04\) |
| `Integer` | Rappresenta un numero intero \(ad esempio 5 oppure 234\) |
| `Boolean` | Rappresenta un valore che può solamente essere vero \(_true_\) o falso \(_false_\) e viene solitamente utilizzato nelle operazioni logiche |
| `String` | Rappresenta un elemento di testo \(ad esempio "ciao"\) |
| `Vector3` | Rappresenta un set di 3 coordinate \(x, y, z\) e può essere utilizzato per indicare, tra le altre cose, posizione o direzione di un oggetto |
| `GameObject` | Rappresenta l'entità base degli oggetti in una scena Unity |

### Le Variabili

Una _variabile_, in informatica, è una sorta di "cassetto" nella memoria il cui scopo è di contenere un valore \(un numero, una stringa, un gameobject\). Una variabile in Bolt è individuata da un nome identificativo.

Bolt permette di creare \(dichiarare\) sei tipi di variabili:

| Tipo | Descrizione |
| :--- | :--- |
| **Flow Variables** | Sono variabili utilizzate localmente all'interno di un Flow Graph |
| **Graph Variables** | Sono dichiarate localmente all'interno di un Flow Graph e non possono essere viste esternamente dal grafo dove vengono utilizzate  |
| **Object Variables** | Appartengono ad un gameobject e possono essere utilizzate da qualsiasi grafo del gameobject stesso. Possono essere utilizzate per esporre parametri modificabili |
| **Scene Variables** | Sono variabili visibili da qualsiasi oggetto in scena |
| **Application Variables** | Sono variabili persistenti da una scena all'altra e verranno "eliminate" solamente se l'applicazione viene chiusa |
| **Saved Variables** | Sono variabili che vengono salvate anche se l'applicazione viene chiusa. Utilizzano il sistema di salvataggio di Unity |

