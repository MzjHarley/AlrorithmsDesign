|Author|Date|
|---|---|
|MZJ|2022/4/15|
---

# 0-1KnapStack

Example：There are 5 items，their weight  {2,2,6,5,4},value is {6,3,5,4,6},the bag's capacity is 10.Please solving the 0-1 KnapStack problem. 

![contents](https://github.com/MzjHarley/AlrorithmsDesign/blob/main/IMG/2.png)  
**TotalValue:the bag's item total value.  
i:the item 's serial number.                    
j:the bag's capacity.                               
v[i]:the item i 's value.                              
w[i]:the item i's weight.**

|i|w[i]|v[i]|
|---|---|---|
|1|2|6|
|2|2|3|
|3|6|5|
|4|5|4|
|5|4|6|

|i\j|0|1|2|3|4|5|6|7|8|9|10|
|---|---|---|---|---|---|---|---|---|---|---|---|
|0|0|0|0|0|0|0|0|0|0|0|0|
|1|0|0|**6**|6|6|6|6|6|6|6|6|
|2|0|0|**6**|6|9|9|9|9|9|9|9|
|3|0|0|6|6|9|9|**9**|9|11|11|14|
|4|0|0|6|6|9|**9**|9|10|11|13|14|
|5|0|0|6|6|**9**|9|9|12|12|15|15|
