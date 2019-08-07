[link](https://medium.com/swlh/the-ultimate-strategy-to-preparing-for-the-coding-interview-ee9f7eb439f3#0330)

    keyword: I was not solving coding problems but practicing to 'map' problems to already known problems that i've solved before.

Map the given problem to solved problem.

* if the given input is sorted (array, list or matrix), then we will be using a variation of `Binary Search` or a `Two Pointers strategy`

* if we ar dealing with top / maximum / minimum / closest k elements among n elements, we will be using a `Heap`.

* if we need to try all combination(or permutations) of the input, we can either use recursive Backtracking or iterative Breadth-First Search

* Most of the questions related to Trees or Graphs can be solved either through Breadth-First Search or Depth-First Search.

* Every recursive solution can be converted to an iterative solution using a stack.

* If for a problem, there exists a brute-force solution in O(n2) time and O(1) space, there must exist two other solutions: 1) using a Map or a Set for O(n) time and O(n) space, 2) using sorting for O(nlogn) time and O(1) space.

* If the problem is asking for optimization (e.g., maximization or minimization), we will need to use Dynamic Programming to solve it.

* If we need to find some common substring among a set of strings, we will be using a HashMap or a Tree.

* If we need to search among a bunch of strings, Tree will be the best datastructure.

* If the problem involves a LinkedList and we can't use extra space, then use Fast & Slow Pointer approach.


### Binary Search

  1. Bitonic Array Maximum
