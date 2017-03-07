# LA Sort
===================================
LA Sort is a sorting algorithm that attempts to achieve a O(kn) time and O(kn) space complexities, where 'k' is a constant and is far less than 'n'.

The algorithm achieves this by aligning the numbers as close to sequential numbers as possible. Once aligned, since the numbers are sequential, they can be ordered consecutively.

# Approach
===================================
Consider the following set of numbers:

_12, 18, 53, 8, 19, 26, 80, 34, 92_ |
-----------------------------------

In order to align them as close to being sequential as possible:
* shift the numbers to start at 0:
    * sweep through the numbers once to find the min and max
    * subtract minimum from all the numbers
* shrink the numbers smaller values
    * divide each number by a factor, which is (max - min) / (n - 1)

If the original numbers were evenly distributed, then after dividing them by the factor, they will coalesce and be much closer to being sequential and starting at 0, than the original numbers were.

Then, separate these newly coalesced numbers into buckets, each of size 'k', such that:
* all numbers in a bucket are sorted
* all numbers in a bucket (m) are less than all numbers in bucket (m+1)
* all numbers in a bucket (m) are greater than all numbers in bucket (m-1)

Finally, join all the n/k buckets in order.