# Complessità dei problemi
> [!NOTE]
> ## Ogni problema ha una complessità che ha un limite superiore ed inferiore.
>>     Il senso è che il problema può essere Theta n
>>     perché c'è una soluzione che ha complessità Theta.
>>     Ma ogni altra soluzione/algoritmo più lento è comunque una soluzione 
>>     con complessità diversa.
> Se una soluzione è più veloce del limite inferiore questo significa che:
> - 1 La soluzione che hai trovato è sbagliata
> - 2 Hai trovato un nuovo limite inferiore
>
> ## Come definire un limite inferiore? `Spoiler: è piuttosto difficile`
> - Per la maggior parte delle volte è il problema a dirtelo
>>     La somma di tutti i numeri fino a N deve essere Omega N
> *Ricorda la differenza tra problemi che usano confronti e problemi che non lo fanno.*
> ### Ci sono problemi che non possono essere risolti in un tempo polinomiale.
>
> ### Albero decisionale `(ricerca per confronto)`
> È un albero dove ogni nodo interno è un confronto e le foglie sono gli output. `La lunghezza dell'albero è Log(n)`
>
> Per questo motivo ordinare per comparazione è almeno *n*log(n)*.
>

> [!TIP]
> Quando scriviamo log(n) ignoriamo la base del logarimo perché dipende dalla base dell'albero che potrebbe essere non binario ma terziario o più.
> 
> *-Consiglio di guardare i pdf del professore per avere una spiegazione più completa e dettagliata degli argomenti.*
