#LA Sort
LA Sort is a sorting algorithm that attempts to achieve a O(kn) time and O(kn) space complexities, where 'k' is a constant and is far less than 'n'.

The algorithm achieves this by aligning the numbers as close to sequential numbers as possible. Once aligned, since the numbers are sequential, they can be ordered consecutively.

#Approach
Consider the following set of numbers:

_12, 18, 53, 8, 19, 26, 80, 34, 92_


In order to align them as close to being sequential as possible:
* shift the numbers to start at 0:
    * sweep through the numbers once to find the min and max
        * 8 and 92, respectively
    * subtract minimum from all the numbers
        * _4, 10, 45, 0, 11, 18, 72, 26, 84_
* shrink the numbers smaller values
    * divide each new number by a factor, which is (new max) / (n - 1)
        * (new max) = (84) / (9 - 1) = 84 / 8 = 10
        * _0, 1, 4, 0, 1, 1, 7, 2, 8_

Once the numbers have been aligned, move them in respective buckets and then sort individual bucket.
* based on the new numbers, assign the original numbers in respective buckets
    * if k = 5, there will be two buckets
    * the new numbers will be split to have:
        * _0, 1, 0, 1, 1_ in bucket 1
        * _4, 7, 2, 8_ in bucket 2
    * after the split, the numbers in each bucket will be in such a way that:
        * all numbers in a bucket (m) are less than all numbers in bucket (m+1)
        * all numbers in a bucket (m) are greater than all numbers in bucket (m-1)
* since the buckets have at the most 'k' elements, it is easier to sort them as-is
* once all the numbers in each bucket are sorted, then join the buckets in order of their indices.
