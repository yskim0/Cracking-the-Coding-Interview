## Part 1. Data Structures
#### 📔 Ch 1. Arrays and Strings

Q1~Q3: simply solved by using `set`. 

Q4: ***anagrams***

Q5: `str.replace` contains time complexity of O(N^2).

Q6: Given an image represented by an NxN matrix, where each pixel in the image is 4 bytes, write a method to rotate the image by 90 degrees Can you do this in place. 


```py
import numpy as np
m, n = map(int, input().split())
arr = np.random.randint(0,10, (m, n))
a_ = arr[::-1]
for i in range(n):
    for j in range(m):
        print(a_[j][i], end = " ")
    print()
```

`np.rot90`도 있고, counterclockwise인지 아닌지도 주의할 것


Q7. Write an algorithm such that if an element in an MxN matrix is 0, its entire row and column is set to 0.

```py
d = {(i,j) : arr[i][j] for j in range(n) for i in range(m)}
from collections import defaultdict
inverted_dict = defaultdict(list)
{inverted_dict[v].append(k) for k, v in d.items()}
for row_idx, col_idx in inverted_dict[0]:
    arr[row_idx, :] = 0
    arr[:, col_idx] = 0
```
- `defaultdict`: 인자로 객체의 기본값을 딕셔너리의 초기값으로 지정할 수 있다.
    - 언제 유용한가? 키의 개수를 세야 하는 경우, 리스트나 셋의 항목을 정리해야 하는 경우. 


Q8. Assume you have a method isSubstring which checks if one word is a substring of another Given two strings, s1 and s2, write code to check if s2 is a rotation of s1 using only one call to isSubstring (i e , “waterbottle” is a rotation of “erbottlewat”).

```
isString(s1+s1, s2)
```
- 고전 문제라서 해당 풀이를 외워두면 될 것 같다.
- O(N)
