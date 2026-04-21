# 4.7 Distributed Data Processing

This section examines how large datasets are processed across multiple machines using the MapReduce framework. The approach combines "pure functions that are used to map over a large dataset and then to reduce the mapped sequences of values into a final result."

## Key Advantages of MapReduce

The framework enforces separation between two concerns:

1. Map and reduce functions that process and combine data
2. Communication and coordination between machines

This abstraction hides distributed computing complexities from developers, handling machine failures, network issues, and progress monitoring automatically.

## 4.7.1 MapReduce Process

The framework operates in three steps:

1. A map function processes each input, outputting zero or more intermediate key-value pairs
2. Intermediate pairs are grouped by key
3. A reduce function combines values for each key, outputting final results

The system creates map tasks (applying the map function to data subsets) and reduce tasks (grouping and reducing by key). Multiple mappers and reducers run in parallel, with a sort phase between them organizing pairs by key.

### Example: Vowel Counting

```python
def count_vowels(line):
    """A map function that counts the vowels in a line."""
    for vowel in 'aeiou':
        count = line.count(vowel)
        if count > 0:
            emit(vowel, count)
```

The reduce function uses Python's built-in `sum()` to aggregate counts.

## 4.7.2 Local Implementation

A minimal MapReduce implementation uses Unix pipes and programs. A Python script becomes executable with:

```python
#!/usr/bin/env python3

import sys

for line in sys.stdin:
    print(line.strip('\n')[::-1])
```

Programs are connected via the pipe operator (`|`), chaining output to input.

### Full Application

```bash
$ cat input | ./mapper.py | sort | ./reducer.py
```

### Mapper Implementation

```python
#!/usr/bin/env python3

import sys
from mr import emit

def count_vowels(line):
    """A map function that counts the vowels in a line."""
    for vowel in 'aeiou':
        count = line.count(vowel)
        if count > 0:
            emit(vowel, count)

for line in sys.stdin:
    count_vowels(line)
```

### Reducer Implementation

```python
#!/usr/bin/env python3

import sys
from mr import values_by_key, emit

for key, value_iterator in values_by_key(sys.stdin):
    emit(key, sum(value_iterator))
```

### Sample Output

Given input file `haiku.txt`:
```
Google MapReduce
Is a Big Data framework
For batch processing
```

Execution:
```bash
$ cat haiku.txt | ./count_vowels_mapper.py | sort | ./sum_reducer.py
'a'   6
'e'   5
'i'   2
'o'   5
'u'   1
```

## 4.7.3 Distributed Implementation

Hadoop provides an open-source MapReduce implementation for clusters. Key advantages over local implementation:

- **Speed**: Parallel execution across multiple machines
- **Fault tolerance**: Failed tasks are recomputed automatically
- **Monitoring**: User interface tracks application progress

### Running with Hadoop

```bash
$ python3 mr.py run count_vowels_mapper.py sum_reducer.py [input] [output]
```

The mapper and reducer scripts work directly with Hadoop's streaming interface without modification.


---

## Same Chapter

- [Ch4 1 Introduction](ch4-1-introduction.md)
- [Ch4 2 Implicit Sequences](ch4-2-implicit-sequences.md)
- [Ch4 3 Declarative Programming](ch4-3-declarative-programming.md)
- [Ch4 4 Logic Programming](ch4-4-logic-programming.md)
- [Ch4 5 Unification](ch4-5-unification.md)
- [Ch4 6 Distributed Computing](ch4-6-distributed-computing.md)
- [Ch4 8 Parallel Computing](ch4-8-parallel-computing.md)
