Input file: ~100000 strings with average length ~6000

# Quicksort

Flat profile:

Each sample counts as 0.01 seconds.

|  % time  | cumulative seconds  | self seconds | calls |  self ns/call |   total ns/call | name  | 
| --- | ----------  | ----- | --------- | ------ | ------ | --- |
| 63.22|      0.90    | 0.90  |2269530   |398.32   |398.32  |lexCmp|
| 37.23 |     1.44    | 0.53  |          |          |       |prints|


Call graph

granularity: each sample hit covers 2 byte(s) for 0.70% of 1.44 seconds

|index| % time| self| children|  called |       name          |
|-----|-------|-----|---------|---------|---------------------|
|     |       | 0.90|  0.00| 2269530/2269530|     quickSort [2]|
|[1]  |  62.9 | 0.90|  0.00| 2269530|         lexCmp [1] |
|     |       |     |      |        |                       |
|     |       |     |      |   90379 |          quickSort [2]|
|[2]  |  62.9 | 0.00| 0.90 | 0+90379 |  quickSort [2] |
|     |       | 0.90| 0.00 |2269530/2269530|     lexCmp [1] |
|     |       |     |      |   90379       |      quickSort [2] |
|     |       |     |      |         |                        |
|[3]  |  37.1 |0.53 | 0.00 |          |    prints [3] |


# Merge sort

Flat profile:

Each sample counts as 0.01 seconds.
| % time | cumulative seconds | self seconds |   calls   | self ms/call  | total ms/call | name | 
|------|---------|-------|---------|--------|-------|----------|
|57.19 |    2.93 |   2.93|         |        |       | main     |
|41.52 |   5.05  |  2.13 | 101559  |  0.02  |  0.02 |prints|
| 0.98 |    5.10 |   0.05| 1562440 |   0.00 |   0.00| lexCmp|
| 0.59 |    5.13 |   0.03|  101558 |   0.00 |   0.00| merge|
| 0.00 |    5.13 |   0.00|       1 |   0.00 |  80.23| _sort|
| 0.00 |    5.13 |   0.00|       1 |   0.00 |  80.23| mergeSort|


Call graph

granularity: each sample hit covers 2 byte(s) for 0.19% of 5.13 seconds

|index| %time | self| children|   called    |name                  |
|-----|-------|-----|---------|-------------|----------------------|
|[1]  |100.0  | 2.93|   2.21 |              |main [1]|
|     |       | 2.13|   0.00 | 101559/101559|     prints [2]|
|     |       | 0.00|   0.08  |    1/1      |    mergeSort [4]|
|     |       |     |        |             |               |
|     |       | 2.13|   0.00 |101559/101559|     main [1] |
|[2]  | 41.4  | 2.13|   0.00 |101559       | prints [2]   |
|     |      |      |        |             |                  |
|     |       | 0.03|   0.05| 101558/101558|     _sort [5]|
|[3]  |  1.6  | 0.03|   0.05| 101558       | merge [3]|
|     |       | 0.05|   0.00|1562440/1562440|    lexCmp [6]|
|     |       |     |       |             |              |
|     |       | 0.00|   0.08|      1/1    |     main [1]|
|[4]  |  1.6  | 0.00|   0.08|      1      |  mergeSort [4]|
|     |       | 0.00|   0.08|      1/1    |      _sort [5]|
|     |       |     |       |             |              |
|     |       |     |       | 203116       |      _sort [5]|
|     |       | 0.00|   0.08|      1/1     |      mergeSort [4]|
|[5]  |  1.6  | 0.00|   0.08|      1+203116| _sort [5]|
|     |       | 0.03|   0.05| 101558/101558|     merge [3]|
|     |       |     |       | 203116       |     _sort [5]|
|     |       |     |       |              |              |
|     |       | 0.05|   0.00|1562440/1562440|    merge [3]|
|[6]  |  1.0  | 0.05|   0.00|1562440        |lexCmp [6]       |
