# N-Queen

## 문제 설명

가로, 세로 길이가 n인 정사각형으로된 체스판이 있습니다. 체스판 위의 n개의 퀸이 서로를 공격할 수 없도록 배치하고 싶습니다.

예를 들어서 n이 4인경우 다음과 같이 퀸을 배치하면 n개의 퀸은 서로를 한번에 공격 할 수 없습니다.

![Imgur](https://i.imgur.com/lt2zdK6.png)
![Imgur](https://i.imgur.com/5c5EUrq.png)

체스판의 가로 세로의 세로의 길이 n이 매개변수로 주어질 때, n개의 퀸이 조건에 만족 하도록 배치할 수 있는 방법의 수를 return하는 solution함수를 완성해주세요.

### 제한사항

- 퀸(Queen)은 가로, 세로, 대각선으로 이동할 수 있습니다.
- n은 12이하의 자연수 입니다.

------

### 입출력 예

| n    | result |
| ---- | ------ |
| 4    | 2      |



## 문제 풀이

이번 문제는 DFS 알고리즘을 이용해 모든 경우를 탐색한다. quuen 리스트는 각 인덱스를 열, 원소값을 행이라고 생각한다. 즉 queen = [0, 2, 3, 1] 이라면 퀸은 (0,0) (1,2) (2,3) (3,1) 위치에 있다는 것을 나타낸다.

`queen[row] = col`을 통해서 각 열에 행의 값을 추가한다. x는 range(col)의 값 중 하나이기 때문에 세로로 겹치는 경우는 존재하지 않지만, 가로로 겹치는 경우가 있으면 문제의 조건을 만족하지 못하므로 `queen[x] == queen[col]`을 이용해 같은 행에 존재하는 케이스를 제거한다.

대각선에 위치한 queen 또한 없어야 하므로 `abs(queen[x]-queen[col]) == (col-x)`을 이용해 대각선 위치에 존재하는 queen의 유무를 파악한다. 이런 조건을 사용하는 이유는 **col-x** 는 세로 증가량, **abs(queen[x]-queen[col])**은 가로방향의 증가량을 의미한다. 즉 가로, 세로 증가량이 같으면 기울기 1의 대각선 방향으로 문제 조건을 만족하지 못한다.

모든 열을 돌면서 조건을 만족하는 행의 위치에 퀸을 두게 된다면 1을 리턴해 count에 더해질 것이고 최종적으로 count된 1의 개수의 합 만큼 리턴된다.

```python
def dfs(queen, n, col):
    count = 0
    if n == col:
        return 1
    
    for row in range(n):
        queen[col] = row
        for x in range(col):
            if queen[x] == queen[col]:  
                break
            if abs(queen[x]-queen[col]) == (col-x):
                break
        else:
            count += dfs(queen, n, col+1)

    return count

def solution(n):
    queen = [0]*n
        
    return dfs(queen, n, 0)
```

