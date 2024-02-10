# Hash

***L'hashing è la soluzione ad un sacco di cose... ma non a tutte.***

## Tabelle Hash
> [!WARNING]
> ### [Array associativi](../Trees/[IT]Alberi.md#array-associativo-map-or-dictionary)

> [!NOTE]
> 
>      Le tabelle hash creano un array associativo, ma inserimento, ricerca e cancellazione non sono fatti per comparazione.
>      Caso peggiore Theta n, caso medio è Theta 1.
> **Cose da tenere a mente:**
> - Tipo di chiave
> - Quantità di chiavi
>
>       Prima hai un numero enorme di chiavi, ma a runtime ne usi meno.
>       Poi hai bisogno di una funzione di hash che converte la chiave in un indice per
>       fare un accesso in un array Theta 1.
>  **Se 2 o più chiavi collidono nello stesso indice, c’è una soluzione ma rallenterà a Theta n**
> - Usando una lista
>   
>  **Hashmap = Hash chiave (Theta 1) + Equal (Theta ?) ->**

## Funzioni Equal
Controlla che hai trovato l’elemento giusto nella lista se le chiavi collidono.
- *Theta n*  `deve essere veloce, ma dipende dalla chiave da Theta 1 a n`
  
La crescita in caso di collisione delle chiavi rallenterà a Theta n.

## Funzioni di Hash
> [!TIP]
> Ci sono diverse funzioni e ognuna funziona in modo diverso ma possiamo immaginare che ci sia una scatola nera
> e sappiamo solo che con un input ottieni un output.
> - *Deterministica* `stesso input stesso output`
> - *Theta 1*  `deve essere veloce`
> - *Distributione uniforme * `ogni Hash(chiave)=indice ma a meno che non conosci il risultato ci sono uguali probabilità`
> - *Fattore di carico*
>>     n = elementi inseriti, m = intervallo di indici.
>>     se n/m = 1 ogni slot è usato solo da 1 elemento
>>     se n/m > 1 più elementi degli slot
>>     se n/m < 1 meno elementi degli slots
>>     n/m = Alpha può essere usato per descrivere la velocità
> Quando Alpha si avvicina troppo a un valore specifico raddoppiamo il m, ma facendo così possiamo mantenere Theta 1
> dividendo il costo con le inserzioni passate (Theta 1) nel tempo, come sulla [complessità ammortizzata](../Lists/[IT]Liste.md#crescita-telescopica--complessità-ammortizzata).

## Le funzioni di hash per diversi tipi di dati non sono incluse..

## Soluzione alle collisioni
> [!IMPORTANT]
> - Usando una lista
>   - Costo  
>     - Spazio extra
>     - La funzione Equal può essere lenta
> - Usando l’indirizzamento aperto
>   - Pro
>     - Non usa spazio extra
>     - Alpha (n/m) <= 1 `m+1 inserimenti generano overflow o crescita telescopica`
>     - Può essere fatto senza usare puntatori
>>     Come funziona?
>>     Se avviene una collisione, cerca uno slot libero che può essere trovato dall'inizio o vicino all'indice.
> Si usa una ***Funzione di Scansione***:
>>     Prendi un indice da 0 a m finché non ne trovi uno vuoto, altrimenti overflow.
> [!CAUTION]
> ***Cancellare***  per l’indirizzamento aperto è critico, per questo motivo preferiamo usare questa soluzione quando non abbiamo bisogno di *cancellare*.
>
> Complessità di ricerca fino a (1/Alpha)*ln(1/(1-Alpha))

## Funzione di Scansione
> [!NOTE]
> - Lineare
>    - hash(k)+1 mod(m) `da indice+1 mod m fino a trovare`
> - Quadratica
>    - hash(k)+ ***c1*** + ***c2^2*** mod(m) `c1, c2 dipendono da m`
> - Doppio Hash
>    - hash1(k) + ***i*** * Hash2(k) mod(m)
>>     Hash1, Hash2 entrambe ausiliarie, ma il primo tentativo è usando Hash1.
>>     Serve Hash2(K) > 0 e Hash2(K) deve essere primo con m.
>>     Ogni chiave produce sequenze di indici diverse, fino a m^2 combinazioni.
>>     
