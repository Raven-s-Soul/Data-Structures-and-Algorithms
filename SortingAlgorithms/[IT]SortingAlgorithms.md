# Algoritmi di ordinamento
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
>     - [Heap sort](SortingAlgorithms.md#heap-sort)
> ## Properties
> - *on site* `do not need extra space`
> - *stable* `don't swap the order of object with the same value`
> - *adaptive* `faster with a part already ordered`
> - *online* `can be used when the numbers come one at a time`
> - *effective on small instances*
>
> ## Recurrence formula
> Equations or inequalities that describe a function and its value on smaller inputs.
> ## Divide Et Impera
> - Cut the problem in smaller and simpler ones
> - [Iterative](SortingAlgorithms.md#greedy)
>   -  [Merge Sort](SortingAlgorithms.md#merge-sort)
>   -  [Quick Sort](SortingAlgorithms.md#quick-sort)
> ## Master theorem
> - a,b > 1 
> - a number of sub-substance 
> - b number of the element in the sub.
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
>  -  *is not on site*
>  -  *is stable*

## Quick Sort
>  [!NOTE]
> Ex: Split the array in two where every element of 1 array is <= elements of the second, then order and combine.
>>     Array 1 has from p to q-1, and Array 2 has from q+1 to r
>>     if p = r is already ordered, if p > r should be an error.
> You need for the split a value q that is got for *PARTITION* of the array using the lower and highest value.
>
> How *PARTITION* work? **Theta n**
>   - Get the element with max index = Arrat[r]
>   - Count how many are <= of that element, the sum is q
>       - Swap Array[counter] with Array[q] and q++ 
>   - End loop, swap Array[q] with Array[r] and return q.
>>     When you get q you can Quick_Sort(Array,p,q-1) and Quick_Sort(Array,q+1,r).
> ###  Theta n*log(n) or Theta n^2
>  -  *[Divide Et Impera](SortingAlgorithms.md#divide-et-impera)*
>  -  *is on site*
>  -  *is not stable*

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
>  Remember Heap and priority queues!
>
>  How it works:
>  - You make from an array a tree, and take the array size.
>  - Inside the loop:
>      -  you swap the values inside of index 0 to the iterator
>      -  each time and use *heapify* for be sure to have the one with the priority on top.
>      -  then you decrease the iterator since you already did the swap on that value.
>
> 
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
>  How it works:
>  - You make a tree.
>  - Inside the loop that iter the size of the array to sort:
>      -  Insert the value of the array in the binary tree.
>      -  `keeping always left smallest and right bigger values` 
>  -  You read from the order you prefer the tree and insert in the Array
> ### 
>  - Theta n^2 (not balanced)
>  - Big-O(n log n) (balanced)
>  - [Wiki](https://en.wikipedia.org/wiki/Tree_sort)
>  - *is not on site*

##  Counting Sort
>  [!NOTE]
>  - There are K counters for each avaible value ***i***
>  - for every ***i*** count how many input are the same as ***i***
>  - how many input are less then ***i***
>  - then place the ***i*** elements in the right spot on the array.
>
>  **All operation are Theta n**
>  - *is stable*
>  - *is not on site*
>  - *is not online*
>  - ***Theta n+k***

##  Bucket Sort
>  [!NOTE]
>  - Make a list for evert ***i*** <= k
>  - Reed the Array and insert the value on the list that corresponds to it's value
>  - Then empthy the list filling the array
> 
>  **All operation are Theta n**
>  - *is stable*
>  - *is not on site*
>  - *is not online*
>  - ***Theta n+k***

##  Radix Sort
>  [!NOTE]
>  We want to order values that we suppose have a sequence of ***d*** digits
>
>     When we want to sort based on multiple criteria we must first consider
>     the least significant criteria and then the most significant criteria
>  - Sort for each ***d*** sort.
> 
>  **All operation are Theta n**
>  - *is stable*
>  - ***Theta d(n+k)*** `k is max value in the digit`
