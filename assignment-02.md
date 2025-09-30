# CMPS 2200 Assignment 2

**Name:**_________________________

In this assignment we'll work on applying the methods we've learned to analyze recurrences, and also see their behavior
in practice. As with previous
assignments, some of of your answers will go in `main.py` and `test_main.py`. You
should feel free to edit this file with your answers; for handwritten
work please scan your work and submit a PDF titled `assignment-02.pdf`
and push to your github repository.


## Part 1. Asymptotic Analysis

Derive asymptotic upper bounds of work for each recurrence below.

* $W(n)=2W(n/3)+1$ 
. a = 2 
. b = 3
. f(n) = 1 
. n^logb(a) = n^log3(2) = n^0.63
. f(n) = 1 = O(1) -> O(1) < n^0.63
. Case 1 of Master Theorem 
. Upper bounds of work = W(n) = Θ(n^log3(2))
 
* $W(n)=5W(n/4)+n$
. a = 5 
. b = 4
. f(n) = n 
. n^logb(a) = n^log4(5) = n^1.16
. f(n) = n = O(n) -> O(n) < n^1.16
. Case 1 of Master Theorem  
. Upper bounds of work = W(n) = Θ(n^log4(5))

* $W(n)=7W(n/7)+n$
. a = 7 
. b = 7
. f(n) = n 
. n^logb(a) = n^log7(7) = n^1 = n
. f(n) = n = O(n) -> O(n) = n^1
. Case 2 of Master Theorem 
. Upper bounds of work = W(n) = Θ(n log n)

* $W(n)=9W(n/3)+n^2$
. a = 9 
. b = 3
. f(n) = n^2
. n^logb(a) = n^log3(9) = n^2 
. f(n) = n^2 = O(n^2) -> O(n^2) = n^2
. Case 2 of Master Theorem 
. Upper bounds of work = W(n) = Θ(n^2 log n) 

* $W(n)=8W(n/2)+n^3$
. a = 8 
. b = 2
. f(n) = n^3 
. n^logb(a) = n^log2(8) = n^3 
. f(n) = n^3 = O(n^3) -> O(n^3) = n^3 
. Case 2 of Master Theorem 
. Upper bounds of work = W(n) = Θ(n^3 log n)

* $W(n)=49W(n/25)+n^{3/2}\log n$
. a = 49 
. b = 25 
. f(n) = n^(3/2) log n
. n^logb(a) = n^log25(49) = n^1.21 
. f(n) = n^(3/2) log n = O(n^(3/2) log n) -> O(n^(3/2) log n) > n^1.21
. Case 3 of Master Theorem
. Must meet regularity condition -> a f(n/b) <= c f(n)
. a * f(n/b) = 49 * (n/25)^(3/2) * log(n/25) = 49/25^(3/2)* n^(3/2) * (log n - log 25) -> 49/125*n^(3/2) * (log n - log 25) -> Our coefficient 49/125 = 0.392 which is less than 1 so the regularity condition is met. Upper bound of our work will be O(f(n)).  
. Upper bounds of work = W(n) = Θ(n^(3/2) log n)

* $W(n)=W(n-1)+2$
. Master Theorem does not apply here because the reccurence shrinks additively, and not multipicatively. Each recursive step reduces n by 1 and our work done outside of the recursive call is constant (f(n) = 2), so the recursion tree has depth of Θ(n). This means our upper bound of work will be W(n) = Θ(n). 
. 
. 
.  
. 
.  
.  
.  

* $W(n)= W(n-1)+n^c$, with $c\geq 1$
. Same as the previous example, the Master Theorem does not apply because recurrence shrinks additively. However, our outside work f(n) is different here. The recursion tree still has a depth of Θ(n), however f(n) = n^c with c >= 1. In this case, if c = 1, our work is W(n) = n + (n - 1) + (n - 2) + ... + 1 = Θ(n^2). Similarly, if c = 2, our work is W(n) = n^2 + (n - 1)^2 + (n - 1)^3 + ... + 1^2 = Θ(n^3). From this, we can assume if we are raising n to the c power, our work will be Θ(n^(c+1)).
.  
.  
.  
.  
. 
.  
. 

* $W(n)=W(\sqrt{n})+1$
. We can change sqrt(n) to n^(1/2). We can define a new variable n in which n = 2^m, and m = log2(n). From this, we can define an instance S where S(m) = W(2^m) and W(2^m^(1/2)) + 1 = W(2^(m/2)) + 1 = S(m/2) + 1. Now, we have an additive-halving recurrence formula of S(m) = S(m/2) + 1. This is a regular halving recurrence so after k steps, m/2^k, 2^k = m, k = log2(m), so S(m) = Θ(log m). From what we established earlier, m = log2(n). We can plug this back to get S(log2(n)) = Θ(log(log(n))). So, our upper bound of W(n) = W(sqrt(n)) + 1 is Θ(log(log(n))). 
.  
.  
.  
.  
. 
. 


## Part 2. Algorithm Comparison

Suppose that for a given task you are choosing between the following three algorithms:

  * Algorithm $\mathcal{A}$ solves problems by dividing them into
      five subproblems of half the size, recursively solving each
      subproblem, and then combining the solutions in linear time.
    
  * Algorithm $\mathcal{B}$ solves problems of size $n$ by
      recursively solving two subproblems of size $n-1$ and then
      combining the solutions in constant time.
    
  * Algorithm $\mathcal{C}$ solves problems of size $n$ by dividing
      them into nine subproblems of size $n/3$, recursively solving
      each subproblem, and then combining the solutions in $O(n^2)$
      time.

    What are the asymptotic running times of each of these algorithms?
    Which algorithm would you choose?


.  For Algorithm A, a = 5, b = 2, f(n) = Θ(n). n^logb(a) = n^log2(5) = n^2.32. f(n) = Θ(n) and n^1 < n^2.32 so this is Case 1 and runtime of A is Θ(n^2.32).
.  For Algorithm B, this an additive shrink recurrence formula so Master Theorem does not apply. W(n) = 2W(n-1) + Θ(1). This unrolls into W(n) = Θ(2^n) since each level doubles number of subproblems which the depth of recurrence tree is Θ(n) so our growth rate is 2^n. So our runtime of B is Θ(2^n).
.  For Algorithm C, a = 9, b = 3, f(n) = Θ(n^2). n^logb(a) = n^log3(9) = n^2. f(n) = Θ(n^2) and n^2 = n^2 so this is Case 2 and runtime of C is Θ(n^2 * log n)
.  For determining which algorithm I'm choosing, I am ruling out B first because exponential is the worst of the three. Between A and C, A will end up having a longer runtime than C because it has a slightly larger exponent. So I would pick algorithm C. 



## Part 3: Parenthesis Matching

A common task of compilers is to ensure that parentheses are matched. That is, each open parenthesis is followed at some point by a closed parenthesis. Furthermore, a closed parenthesis can only appear if there is a corresponding open parenthesis before it. So, the following are valid:

- `( ( a ) b )`
- `a () b ( c ( d ) )`

but these are invalid:

- `( ( a )`
- `(a ) ) b (`

Below, we'll solve this problem three different ways, using iterate, scan, and divide and conquer.

**3a. iterative solution** Implement `parens_match_iterative`, a solution to this problem using the `iterate` function. **Hint**: consider using a single counter variable to keep track of whether there are more open or closed parentheses. How can you update this value while iterating from left to right through the input? What must be true of this value at each step for the parentheses to be matched? To complete this, complete the `parens_update` function and the `parens_match_iterative` function. The `parens_update` function will be called in combination with `iterate` inside `parens_match_iterative`. Test your implementation with `test_parens_match_iterative`.


. As you iterate from left to right, you want to increment the counter variable if you find '(', or decrement if you find ')'.
. Because of this, the counter must be non-negative at each step since that means a parenthesis was closed before being opened.



**3b.** What are the recurrences for the Work and Span of this solution? What are their Big Oh solutions?

**enter answer here**

.  Work: W(n) = W(n - 1) + O(1), As we iterate through the list, our list of elements to be iterated through decreases by 1 and our outside work is constant for each element (check the character, increment/decrement/ignore). In Big Oh, this equals W(n) = O(n) since we are decreasing work by O(1), then increasing it by O(1) right after, returning work to O(n) for whatever value n is.
. Span: S(n) = S(n - 1) + O(1), As we iterate through the list, 
we update sequentially because there is no parallelism in this example. Our span follows our work, giving us S(n) = O(n) as well.


**3c. scan solution** Implement `parens_match_scan` a solution to this problem using `scan`. **Hint**: We have given you the function `paren_map` which maps `(` to `1`, `)` to `-1` and everything else to `0`. How can you pass this function to `scan` to solve the problem? You may also find the `min_f` function useful here. Implement `parens_match_scan` and test with `test_parens_match_scan`

. Since scan requires an associative binary function (f), a sequence (a), and the left identity of f (id), you can use paren_map to convert our list of strings (mylist) into a list of numbers considering to their value according to the paren_map. We pass this list of numbers to scan which will add them together iteratively, and return the running prefix sums (history) and the final sum (supposed to be 0 if correctly matched). 



**3d.** Assume that any `map`s are done in parallel, and that we use the efficient implementation of `scan` from class. What are the recurrences for the Work and Span of this solution? 

**enter answer here**

.  Work: W(n) = O(n)
.  Span: S(n) = O(log n)




**3e. divide and conquer solution** Implement `parens_match_dc_helper`, a divide and conquer solution to the problem. A key observation is that we *cannot* simply solve each subproblem using the above solutions and combine the results. E.g., consider '((()))', which would be split into '(((' and ')))', neither of which is matched. Yet, the whole input is matched. Instead, we'll have to keep track of two numbers: the number of unmatched right parentheses (R), and the number of unmatched left parentheses (L). `parens_match_dc_helper` returns a tuple (R,L). So, if the input is just '(', then `parens_match_dc_helper` returns (0,1), indicating that there is 1 unmatched left parens and 0 unmatched right parens. Analogously, if the input is just ')', then the result should be (1,0). The main difficulty is deciding how to merge the returned values for the two recursive calls. E.g., if (i,j) is the result for the left half of the list, and (k,l) is the output of the right half of the list, how can we compute the proper return value (R,L) using only i,j,k,l? Try a few example inputs to guide your solution, then test with `test_parens_match_dc_helper`.



. We can compute the proper return value (R, L) using only i,j,k,l by using our understanding of how our unmatched parentheses are recording. For the left half, we have (i, j) and we have (k, l) for the right half. If our left half is ['(', '('], we have (0, 2), and if our right half is [')', ')'], we have (2, 0). This shows the most important of our four letters are j and k. Based on this realization, we should establish a condition for when j > k (more unmatched left in the left half than unmatched right in the right half) and for when k >= j (vice versa). When j > k, there are some lefts remaining unmatched, which we can find by doing l (lefts in right half) + j (lefts in left half) - k (rights in right half). This is essentially j - k, since l is 0 (there are no unmatched lefts in the right half). We are then left with i (all unmatched rights in the left half) and j - k (remaining unmatched lefts).   
. We carry this same logic over for when otherwise is true, unmatched rights in the right half are greater than or equal to unmatched lefts in the left half. Instead of keeping i (all unmatched rights in left half), we will be keeping l (all unmatched lefts in right half). Instead of subtracting j - k, we will subtract k - j (remaining unmatched rights). So, when j > k, we return total unmatched lefts since i is 0 and when k >= j, we return total unmatched rights since l is 0.





**3f.** Assuming any recursive calls are done in parallel, what are the recurrences for the Work and Span of this solution? What are their Big Oh solutions?

**enter answer here**

. Work: W(n) = O(n) 
. Span: S(n) = O(log n)


 
 


