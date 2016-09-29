# Generating Data

This script will generate 3 files with a desired number of integers. The script accepts a command line arguments and can be executed using `python gen_data.py n` where `n` is the desired size of the data set.

The script will output three files, `best_case.txt`, `avg_case.txt` and `worst case.txt`. Best case arranges the numbers from 0 to (n - 1), average case fills the text file with n random integers and worst case has the order (n - 1) to 0

The script can be found [here](https://github.com/Go4Algorithms/python/blob/master/data_generation/gen_data.py)

```python

#!/usr/bin/env python

# Sunny Golovine
# sunny@golovinemail.org
# golovine.org

# This script will generate a data set of a set length
# You can generate either worse case data (descending data set),
# best case data set (ascending data set)
# or an average case data set (random data set)

# Each function takes a size argument and will generate a data set
# with the given length

from random import randint
import sys

def best_case(size):
    f = open('best_case.txt', 'w')
    x = 0
    while x < size:
        f.write(str(x) + '\n')
        x = x + 1
    f.close()

def avg_case(size):
    f = open('avg_case.txt', 'w')
    x = 0
    while x < size:
        f.write(str(randint(0,9999999)) + '\n')
        x = x + 1
    f.close()
def worst_case(size):
    f = open('worst_case.txt', 'w')
    while size > 0:
        f.write(str(size) + '\n')
        size = size - 1
    f.close()
# Wrapper for all functions
def gen(size):
    best_case(size)
    avg_case(size)
    worst_case(size)


if __name__ == "__main__":
    arg = int(sys.argv[1])
    gen(arg)


```
