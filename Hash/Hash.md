# Hash
## Hash Table
> [!WARNING]
> ### [Associative arrays](../Trees/Trees.md#associative-array-map-or-dictionary)

> [!NOTE]
> 
>      Hash tables make and associative array, but insert delete and rearch is not made by comparison.
>      Worst case Theta n, and in the average case is Theta 1.
> **Things to keep in mind:**
> - Key type
> - Key quantity
>
>       First you have an huge number of keys, but on runtime you use less.
>       Then you need an hash function that convert the key into a index for
>       make an access into an array Theta 1.
>  **If 2 or more keys collide into the same index, there is a soluzion but is gonna slow into Theta n**
> - Using a list
>   

## Hash Functions
> [!TIP]
> There are different functions and each work differently but we can immagine there is a black box
> and we know only that with an input you get an output.
> - *Deterministic* `same input same output`
> - *Theta 1*  `need to be fast`
> - *Uniform distribution* `each Hash(key)=index but unless you know the result there are equal chances`
> - *Load factor*
>>     n = elements inserted, m = index range.
>>     if n/m = 1 every slot is used only 1 element
>>     if n/m > 1 more elements then the slots
>>     if n/m < 1 less elemntts then the slots
