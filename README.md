Input file: ~100000 strings with average length ~6000

# Quicksort

Flat profile:

Each sample counts as 0.01 seconds.

|  % time  | cumulative seconds  | self seconds | calls |  self ns/call |   total ns/call | name  | 
| --- | ----------  | ----- | --------- | ------ | ------ | --- |
| 63.22|      0.90    | 0.90  |2269530   |398.32   |398.32  |lexCmp|
| 37.23 |     1.44    | 0.53  |          |          |       |prints|
