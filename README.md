# Coin change with c++

Given a value N, if we want to make change for N cents, and we have infinite supply of each of S = { 1, 2, 5, 50} valued coins, how many ways can we make the change? The order of coins doesn’t matter.

## solution 
1) Optimal Substructure 
To count the total number of solutions, we can divide all set solutions into two sets. 
1) Solutions that do not contain mth coin (or Sm). 
2) Solutions that contain at least one Sm. 
Let ways_count(S[], m, n) be the function to count the number of solutions, then it can be written as sum of ways_count(S[], m-1, n) and ways_count(S[], m, n-Sm).
Therefore, the problem has optimal substructure property as the problem can be solved using solutions to subproblems. 

2) Overlapping Subproblems 
Following is a simple recursive implementation of the Coin Change problem. The implementation simply follows the recursive structure mentioned above.

3) Approach (Algorithm)

See, here each coin of a given denomination can come an infinite number of times. (Repetition allowed), this is what we call UNBOUNDED KNAPSACK. We have 2 choices for a coin of a particular denomination, either i) to include, or ii) to exclude.  But here, the inclusion process is not for just once; we can include any denomination any number of times until N<0.

Basically, If we are at s[m-1], we can take as many instances of that coin ( unbounded inclusion ) i.e ways_count(S, m, n – S[m-1] ) ; then we move to s[m-2]. After moving to s[m-2], we can’t move back and can’t make choices for s[m-1] i.e ways_count(S, m-1, n ).

Finally, as we have to find the total number of ways, so we will add these 2 possible choices, i.e ways_count(S, m, n – S[m-1] ) + ways_count(S, m-1, n ) ;

which will be our required answer.
