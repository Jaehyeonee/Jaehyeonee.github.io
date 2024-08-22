---
title: 백준11931 수 정렬하기4/백준15688 수 정렬하기5
author: jaehyeonee
date: 2024-08-21 11:50:00 +0800
categories: [BOJ, Algorithm]
tags: [BOJ]
pin: true
math: true
mermaid: true
# image:ㄴ
#   path: 
#   lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
#   alt: Responsive rendering 
---

## BOJ 11931 수 정렬

문제 링크
[BOJ11728](https://www.acmicpc.net/problem/11931)

```python
import sys
input = sys.stdin.readline

n = int(input())

num = list(int(input()) for _ in range(n))
num.sort(reverse = True)

for i in range(n):
    print(num[i])
```

## BOJ 15688 수 정렬5
문제 링크
[BOJ11728](https://www.acmicpc.net/problem/15688)

> 처음에 음수에 대한 처리를 제대로 하지 못함. 
**sort() 대신 sorted() 함수를 사용한 이유**
: 둘다 음수와 양수를 모두 지원하지만 반환 값에 차이를 가진다.

### sort() vs sorted()
- __sort()__ 는 리스트를 직접 수정하여 정렬된 리스트를 반환하지 않고 ‘None’ 을 반환함.
메모리가 효율적이며 정렬 후 원본 리스트가 변경됨.

- 반면 __sorted()__ 는 원본 데이터를 보존하고 정렬된 새로운 리스트를 반환함.

본 문제에서는,
출력값을 한 줄씩 출력해줘야 하기 때문에 sorted를 사용하는 것이 유리했음

### 기본 풀이

```python
import sys
input = sys.stdin.readline
arr=[]
N=int(input())
for _ in range(N):
    arr.append(int(input())
for i in sorted(arr):
    print(i)
```
### 계수 정렬 풀이
계수정렬을 사용하되, 음수 범위를 처리하기 위한 offset값을 지정

```python

import sys
input = sys.stdin.readline

n = int(input())
offset = 1000000  # 음수를 처리하기 위한 오프셋
array = [0] * (2000000 + 1)  # -1000000 ~ 1000000 범위를 모두 처리

for _ in range(n):
    array[int(input()) + offset] += 1  # 입력값에 오프셋을 더해 인덱싱

for i in range(len(array)):
    if array[i] != 0:
        for _ in range(array[i]):
            print(i - offset)  # 출력 시 오프셋을 빼서 원래 값으로 복원
```