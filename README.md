***Summation Explanation***

- Long-double data type: It is reducing rounding error.

- Pairwise summation: It is implementing a divide and conquer approach, sums neighboring pairs first then recursively sums the results.

- Kahan summation: It is maintaing a running correction to comensate for lost low order bits. 

- Knuth summation: It tracks and corrects rounding errors.

***Minimize Error***

- Rounding error: In floating point arithmetic accumulates when adding numbers of vastly different magnitudes.

- Pairwise sum: Reduces the error by always adding numbers of similar magnitude first.

- Kahan and Knuth sum: Explicitly track lost low order bits and correct them.

*** How Global Sum Problem Affects The Parallelization***

- When parallelizing summation, the global sum problem arises: each thread computes a partial sum independently, but adding partial sums together may introduce additional rounding error.

- Pairwise sum: This technique naturally lend themselves to parallelization because summing can be done recursively on subarrays.

- Kahan and Knuth sums: These techniques are more difficult to parallelize efficiently because the error correction depends on the running total.

***Spreadsheet***
https://docs.google.com/spreadsheets/d/1kB2432gM3VrVOV83MTolhbYNyGS2JgjATOdKf2Uxxno/edit?usp=sharing
