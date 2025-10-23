# Parallel-Programming-Assignments

Spreadsheet link: https://docs.google.com/spreadsheets/d/1Ba0Xfiy_Mrg9TbfPksqQMQx4TV7otJREg9zjqctGnaM/edit?usp=sharing

First Modification Line 22: "SoA_type* AoSoA = new SoA_type[num_blocks]" - I added this line to allocate memory for the number of blocks required to store all RGB values.

Second Modification Line 44: "delete[] AoSoA" - I added this line to properly free allocate memory and prevent memory leaks.

Spreadsheet Explanation:
 - V stands for vector length, V controls how many elements are processed in one block.
 - 1K, 10K, 100K, 1M, 10M represent different total array size.
 - This graph shows how the execution time changes for different array sizes and vector lengths.
 - We can see that when the array size gets bigger, the execution time also increases because more    data needs to be processed.
  