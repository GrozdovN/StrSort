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
|     |       |     |      |          |         <spontaneous>|
|[3]  |  37.1 |0.53 | 0.00 |          |    prints [3] |
