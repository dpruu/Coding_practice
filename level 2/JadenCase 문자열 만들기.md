# JadenCase 문자열 만들기

#### 문제 설명

JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다. 문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.

#### 제한 조건

- s는 길이 1 이상인 문자열입니다.
- s는 알파벳과 공백문자(" ")로 이루어져 있습니다.
- 첫 문자가 영문이 아닐때에는 이어지는 영문은 소문자로 씁니다. ( 첫번째 입출력 예 참고 )

#### 입출력 예

| s                       |         return          |
| ----------------------- | :---------------------: |
| "3people unFollowed me" | "3people Unfollowed Me" |
| "for the last week"     |   "For The Last Week"   |



### 문제 풀이

문자열 `s`를 공백을 기준으로 단어를 나눈다. 단어의 앞글자만 대문자로 변환해주는 `capitalize`를 이용해 각 단어들을 앞글자만 대문자로 변환하고 다시 공백을 기준으로 단어들을 `join`한다. 

```python
def solution(s):
    answer = []
    for word in s.split(' '):
        word = word.capitalize()
        answer.append(word)
    answer = ' '.join(answer)
    return answer
```

