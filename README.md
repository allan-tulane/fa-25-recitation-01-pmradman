# CMPS 2200  Recitation 01

**Name (Team Member 1):**_______Petra Radmanovic__________________  
**Name (Team Member 2):**_________________________

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`. All tests are in `test_main.py`.

## Install Python Dependency

We need Python library of "tabulate" to visualize the results in a good shape. Please install it by running 'pip install tabulate' or 'pip install -r requirements.txt' in Shell Tab of Repl.  

## Running and testing your code

- To run tests, from the command-line shell, you can run
  + `pytest test_main.py` will run all tests
  + `pytest test_main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Git" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [x] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [x] 2. Test that your function is correct by calling from the command-line `pytest test_main.py::test_binary_search`

- [x] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [x] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`? 

**TODO: For linear search, the worst key would be the final key (farthest right) or a key larger than the list, for binary search it would be the one with the maximum number of comparisons or the maximum search depth, this is usually the lkey on the farthest end of the list

- [x] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 

**TODO: the best value of key for linear search would be the one equal to the value farthest left in the list or the first index, while in binary serach it would be the exact middle key used for comparisons or the first one we compare or shalowest key

- [x] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [x] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest test_main.py::test_compare_search`, which contains some simple checks.

- [x] 8. Call `print_results(compare_search())` and paste the results here:

**TODO: 
|        n |   linear |   binary |
|----------|----------|----------|
|       10 |    0.001 |    0.001 |
|      100 |    0.002 |    0.001 |
|     1000 |    0.015 |    0.001 |
|    10000 |    0.147 |    0.002 |
|   100000 |    1.534 |    0.002 |
|  1000000 |   15.923 |    0.007 |
| 10000000 |  172.978 |    0.030 |

- [x] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

**TODO: Yes, becuase the linear search is getting continuously bigger as the input is getting bigger, and the difference between the values is also getting much larger, while the logarithmic one has very very little difference between the different values even with an extremely large input, becuase logarithmic graphs do not grow at a constant rate like linear ones, they tend to start to flatten out but never become fully parallel. 

- [x] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? **TODO: it would be n*k
  + For binary search? **TODO: we would first need to sort the list, and then search. to sort it would be n^2, then to serach k times it is log2(n)*k. In total, n^2 + klog2n
  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? **TODO: this question is basically asking when is n^2+klog2n >kn

 n^2+klog2n < kn
 n^2 < kn - klog2n
 n^2 < k(n-log2n)
 n^2/(n-log2n) < k

 so if n is 100, k is about 107 

 