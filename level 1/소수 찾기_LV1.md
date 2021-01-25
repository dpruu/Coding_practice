# 소수 찾기_lv1

1부터 입력받은 숫자 n 사이에 있는 소수의 개수를 반환하는 함수, solution을 만들어 보세요.

소수는 1과 자기 자신으로만 나누어지는 수를 의미합니다.
(1은 소수가 아닙니다.)

##### 제한 조건

- n은 2이상 1000000이하의 자연수입니다.

```python
from math import sqrt

def solution(n):
    decimal = [True] * (n+1)
    
    for number in range(2,int(sqrt(n))+1):
        if decimal[number]  == True:
            for mul in range(2*number, n+1, number):
                decimal[mul] = False
                
    return len([i for i in range(2, n+1) if decimal[i] == True])
```

> 에라토스테네스의 체 알고리즘을 이용해야 한다.  사용하지 않을 경우 시간초과 문제 발생
>
> 구하고자 하는 구간의 소수를 찾는 방법은 2부터 소수로 저장 후 구간내에 존재하는 모든 2의 배수 제거, 그 다음 수인 3도 소수이므로 저장 후 3의 배수 모두 제거한다. 이와 같은 작업을 반복하면 주어진 구간내에 소수만 남게 된다.

## 다른 풀이

```python
def solution(n):
    num = set(range(2,n+1))

    for i in range(2,n+1):
        if i in num:
            num-=set(range(2*i,n+1,i))
    return len(num)
```

> 위와 같이 set을 이용해 만드는 것도 가능하다.