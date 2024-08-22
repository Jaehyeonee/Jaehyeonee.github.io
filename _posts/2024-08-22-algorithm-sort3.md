---
title: 백준10989. 수 정렬하기3 + '계수 정렬'
author: jaehyeonee
date: 2024-08-21 11:40:00 +0800
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

이번 문제를 풀기 위해서는 계수 정렬에 대해 알아야 한다.

계수 정렬에 대해 먼저 짚고 문제를 풀어보자!

계수 정렬에 대해 알기전에, 기본적인 비교 정렬을 생각해보자.

# 이론 

## __비교 정렬__

모든 정렬 알고리즘은 기본적으로 배열의 요소들을 검사하는 과정이 포함되어 있다. <Br>
따라서 배열의 데이터들을 비교하기 위해서 우리는 __Decision Tree__ 를 만들어 경우의 수를 따진다.
그렇기 때문에
decision tree의 높이인 logn 만큼 비교연산이 일어난다.<br> 비교연산의 시간 복잡도는 __O(n)__ 이므로 비교연산을 사용하는 정렬 알고리즘은 아무리 빨라도 __O(nlogn)__ 보다 빠를 수는 없다.<br>
빠른 정렬 알고리즘이라고 알고있는 __퀵 소트, 머지소트__ 역시 __O(nlogn)__ 의 복잡도를 가진다.

## __계수정렬 counting sort__
계수 정렬의 컨셉은 다음과 같다.
<br>
```"비교 연산을 사용하지 않는다면 Decision Tree의 제약사항 없이 더 빠른 정렬이 가능하지 않을까?"```
<br><br>
계수정렬 혹은 counting sort는 이런 아이디어를 기반으로 나온 __O(n+데이터의 최대값 k)__ 의 속도가 보장되는 정렬 알고리즘이다.<br>
countin sort는 이름 그대로 배열 내에 특정한 값이 몇 번 등장했는지에 따라 정렬을 수행하기 때문에 비교연산이 사용되지 않는다.

### counting sort의 구조
  * 입력 배열 ```A```
  * 입력 받은 배열 A의 요소값의 등장 횟수를 저장한 배열 ```B```
  * 최종적으로 정렬된 값들을 담을 배열 ```C```

counting sort의 구조를 파이썬으로 그대로 구현하면 다음과 같다.

```python
# 계수정렬
import sys
input = sys.stdin.readline

n = int(input())

A = list(int(input()) for _ in range(n))
m = max(num) + 1

B = [0] * m
C = [0] * n

for i in range(n):
    B[A[i]] += 1

for i in range(m):
    if i >=1 :
        B[i] = B[i-1] + Bt[i]

for i in range(n-1,-1, -1):
    c = B[A[i]]
    C[c-1] = A[i]
    B[A[i]] -= 1

print(C)
```


계수 정렬에 대한 개념이 확립되었으니 이제 백준 10989 문제를 해결해보자!

## BOJ 10989 수 정렬하기 3 
문제 링크
[BOJ11728](https://www.acmicpc.net/problem/10989)

counting sort 계수정렬을 이용해 풀이 <br>
```→ Օ(n+데이터의 최대값 k)```


```python
### 성공: 올바른 계수 정렬
import sys
input = sys.stdin.readline

#계수정렬 활용
n = int(input())
arr = [0] * (10000 + 1) # 입력값이 10000개까지 주어지니 10000 + 1개의 리스트 선언

#각 입력값에 해당하는 인덱스의 값 증가
for _ in range(n):
    arr[int(input())] += 1
  
#arr에 기록된 정보 확인
for i in range(len(arr)):
    if arr[i] != 0: #0이 아닌 데이터, 즉 입력받은 데이터들을 출력
        for _ in range(arr[i]):
            print(i)
```
### 처음 제출 실패 이유: 
계수 정렬을 사용했으나 메모리 초과로 실패: <br>
아마 max를 사용하고 뒤에서부터 인덱스를 접근하는 것이 문제.
