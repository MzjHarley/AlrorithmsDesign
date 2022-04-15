|Author|Date|
|---|---|
|MZJ|2022/4/15|
---

# 0-1 KnapStack

Example：There are 5 items，their weight  {2,2,6,5,4},value is {6,3,5,4,6},the bag's capacity is 10.Please solving the 0-1 KnapStack problem. 

![contents](https://github.com/MzjHarley/AlrorithmsDesign/blob/main/IMG/3.png)  
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
|5|0|0|6|6|**9**|9|12|12|15|15|15|

```c++
#include <iostream>
using namespace std;

int main()
{
    cout.setf(std::ios::left); // set cout left justify.
    int w[6] = {0, 2, 2, 6, 5, 4}, v[6] = {0, 6, 3, 5, 4, 6}, TotalValue[6][11] = {0}, x[6] = {0};
    // array x：judge item whether in the bag or not.          1 in, 0 not in.
    for (int i = 1; i <= 5; i++)
        for (int j = 1; j <= 10; j++)
            if (j < w[i]) // the bag can't hold item i.
                TotalValue[i][j] = TotalValue[i-1][j];
            else
                TotalValue[i][j] = TotalValue[i-1][j]>TotalValue[i-1][j-w[i]]+v[i] ? TotalValue[i-1][j]:TotalValue[i-1][j-w[i]]+v[i];

    for (int i = 0; i < 6; i++)
    {
        for (int j = 0; j < 11; j++)
        {
            cout.width(3);
            cout << TotalValue[i][j];
        }
        cout << endl;
    }
    cout << TotalValue[5][10] << endl;

    // judge item whether in the bag or not.
    for (int i = 5, j = 10; i > 0; i--)
        if (TotalValue[i][j] > TotalValue[i - 1][j])
        {
            x[i] = 1;
            j = j - w[i];
        }
        else
            x[i] = 0;

    cout << "Ihe bag's items:{";
    for (int i = 1; i < 6; i++)
        cout << x[i] << " ";
    cout << "}";

    return 0;
}
```
