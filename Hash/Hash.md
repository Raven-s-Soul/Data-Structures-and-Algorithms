# Hash

***Hashing is the solution to ton of things... not all.***

## Hash Table
> [!WARNING]
> ### [Associative arrays](../Trees/Trees.md#associative-array-map-or-dictionary)

> [!NOTE]
> 
>      Hash tables make and associative array, but insert delete and search is not made by comparison.
>      Worst case Theta n, and in the average case is Theta 1.
> **Things to keep in mind:**
> - Key type
> - Key quantity
>
>       Initially, you have a large number of keys, but you use fewer at runtime. Then, you need a hash function that converts 
>       the key into an index to access an array in constant time (Theta 1).
>  **If 2 or more keys collide into the same index, there is a soluzion but is gonna slow into Theta n**
> - Using a list
>   
>  **Hashmap = Hash key (Theta 1) + Equal (Theta ?) ->**

## Equal Functions
Chech that you found the right element in the list if keys collide.
- *Theta n*  `need to be fast, but depenods on the key from Theta 1 to n`
  
The growth in case of key collide is gonna slow eventually into Theta n.

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
>>     n/m = Alpha can be used to describe the speed
> When Alpha is getting too close to a specific value we double the m, but doing so can keep Theta 1 by splitting the cost with the past insertions (Theta 1) over time, like on the [complexity amortized](../Lists/Lists.md#crescita-telescopica--complessità-ammortizzata).

## Hash functions for differents data type are not included.

## Solution to collisions
> [!IMPORTANT]
> - Using a list
>   - Cost  
>     - Extra space
>     - Equal function can be slow
> - Using open addressing
>   - Pro
>     - Don't use extra space
>     - Alpha (n/m) <= 1 `m+1 insert generate overflow or telescopic growth`
>     - Can be made without using pointers
>>     How it works?
>>     If a collision happen, look up for a free slot that can be found from the start or near the index.
> A ***Scanning Function*** is used:
>>     Take and index from 0 to m until you find one empthy, else overflow.

> [!CAUTION]
> ***Delete*** for open addressing is critical, that's the reason we prefer using this solution when we don't need to *delete*.
>
> Search complexity up to (1/Alpha)*ln(1/(1-Alpha))

## Scanning Function
> [!NOTE]
> - Linear
>    - hash(k)+1 mod(m) `from index+1 mod m until found`
> - Quadratic
>    - hash(k)+ ***c1*** + ***c2***^2 mod(m) `c1, c2 depends on m`
> - Double Hash
>    - hash1(k) + ***i*** * Hash2(k) mod(m)
>>     Hash1, Hash2 both auxialiary, but the first try is using Hask1.
>>     Need Hash2(K) > 0 and Hash2(K) need to be prime with m.
>>     Every key produce different index sequences, up to m^2 combiantions.
>>     
