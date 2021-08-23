# N개의 최소 공배수

###### 문제 설명

두 수의 최소공배수(Least Common Multiple)란 입력된 두 수의 배수 중 공통이 되는 가장 작은 숫자를 의미합니다. 예를 들어 2와 7의 최소공배수는 14가 됩니다. 정의를 확장해서, n개의 수의 최소공배수는 n 개의 수들의 배수 중 공통이 되는 가장 작은 숫자가 됩니다. n개의 숫자를 담은 배열 arr이 입력되었을 때 이 수들의 최소공배수를 반환하는 함수, solution을 완성해 주세요.

##### 제한 사항

- arr은 길이 1이상, 15이하인 배열입니다.
- arr의 원소는 100 이하인 자연수입니다.



### 문제 풀이

최대 공약수를 구해주는 `math.gcd`함수를 이용해 `arr`에서 두 개의 숫자를 곱하고 최대 공약수로 나누고 나온 값과 `arr`의 다른 숫자들을 같은 과정을 반복해 `arr`의 최소 공배수를 구한다.

```python
from math import gcd

def solution(arr):
    
    answer = arr[0]
    for i in range(1,len(arr)):
        answer = answer * arr[i] // gcd(answer,arr[i])
        
    return answer
```

