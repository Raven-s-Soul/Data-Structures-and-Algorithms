# Sorting Algorithms
> [!TIP]
> ## Disclaimer
> ***Don't trust too much of these code snippets***
> 
> If the sorting code is not accurate feel free to add or change or remove, are just to example of their work.

> [!IMPORTANT]
> ## Greedy
> - This kind of approach look always for the best at the moment, even if isn't worth over time.
>     - [Selection sort](SortingAlgorithms.md#selection-sort)
> ## Iterative
> - The solution of a simple case can help doing a hard one. 
>     - [Insertion sort](SortingAlgorithms.md#insertion-sort)
> ## Properties
> - *on site* `do not need extra space`
> - *stable* `don't swap the order of object with the same value`
> - *adaptive* `faster with a part already ordered`
> - *online* `can be used when the numbers come one at a time`
> - *effective on small instances*
>
> ## Recurrence formula
> 
> ## Divide Et Impera
> - Cut the problem in smaller and simpler ones
> - [Iterative](SortingAlgorithms.md#greedy)
>   -  [Merge Sort](SortingAlgorithms.md#merge-sort)
>   -  [Quick Sort](SortingAlgorithms.md#quick-sort)
> ## Master theorem (teorema dell’esperto)
> - a,b > 1
> - T(n) = { Theta 1                    if n = 0
> -            { a*T(n/b) + O(n^k)   if n > 0
>>     if a < b^k -> T(n) = Theta n^k        | The first level has the most complexity
>>     if a = b^k -> T(n) = Theta n^k log(k) | All level has the same complexity
>>     if a > b^k -> T(n) = Theta n^logb(a)  | The last level has the most complexity

## Selection sort
>  [!NOTE]
> Ex: Always change the value with the lowest avaible then go next.
> ### Theta n^2  
>  -  *[is Greedy](SortingAlgorithms.md#greedy)*
>  -  *is on site*
>  -  *is stable*

## Insertion sort
>  [!NOTE]
> Ex: Slowly try to make order in just a part and with time add the other parts to the one is already ordered.
> ### Best case Theta n and others Theta n^2  
>  -  *[is Iterative](SortingAlgorithms.md#greedy)*
>  -  *is on site*
>  -  *is stable*

## Merge Sort
>  [!NOTE]
> Ex: Split the array in smaller ones till they are just 2 numbers then order and merge with others ordered pairs.
> ###  Theta n*log(n)
>  -  *[Divide Et Impera](SortingAlgorithms.md#divide-et-impera)*
>  -  **

## Quick Sort
>  [!NOTE]
> Ex: 
> ###  
>  -  *[Divide Et Impera](SortingAlgorithms.md#divide-et-impera)*
>  -  **

## [Heap](../Trees/Trees.md#priority-queue-and-heap) Sort
```c
h.A = A; //New Heap
h.size = A.lenght;
Build_Max_Heap(h); //make a heap from an array
for( i = h.A.length-1; i > 1 ; i--) {
  exchange_slots(A,0,i);
  h.size = h.size – 1;
  Max-heapify(h,0); //make node i the highest priority of the sub tree
}
```
>  [!NOTE]
> ### Theta n*log(n)
>  -  *[is Iterative](SortingAlgorithms.md#greedy)*
>  -  *is not stable*
>  -  *is on site*

## [Tree](../Trees/Trees.md#searching) Sort
```c
TREE_SORT(A){
  t.root = NULL;
  for (int i = 1; a < A.length-1; a++){
    INSERISCI(t,A[i]);
  }
  TREE_TO_ARRAY(A,t,0);
}
```
>  [!NOTE]
>  - Theta n^2 (not balanced)
>  - Big-O(n log n) (balanced)
>  - [Wiki](https://en.wikipedia.org/wiki/Tree_sort)
>  - *is not on site*
