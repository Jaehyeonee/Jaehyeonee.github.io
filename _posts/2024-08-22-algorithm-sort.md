---
title: 백준11728. 정렬 알고리즘
author: jaehyeonee
date: 2024-08-21 11:00:00 +0800
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

# 정렬 알고리즘

## BOJ 11728 배열 합치기

이번 문제에서는 여러 풀이를 통해
간단한 정렬 문제에서 풀이 시간을 단축하는 법을 알게되었다.


문제 링크
[BOJ11728](https://www.acmicpc.net/problem/11728)

### - 내 풀이 시간: 1436 ms

```python
# 내 풀이 시간: 1436 ms
import sys
from collections import deque
input = sys.stdin.readline
n, m = map(int, input().split())

list_a = deque(map(int, input().split()))
list_b = deque(map(int, input().split()))

result = deque()

while list_a and list_b:
    if list_a[0] > list_b[0]:
        result.append(list_b.popleft())
    else:
        result.append(list_a.popleft())

ans = result + list_a + list_b

print(' '.join(map(str, ans)))
```

### - 투 포인터 사용 풀이: 2350ms

```python
# 투포인터 2360ms
N,M=map(int,input().split())

A=list(map(int,input().split()))
B=list(map(int,input().split()))

ans=[]

a=0
b=0
while a!=len(A) or b!=len(B):

    if a == len(A):
        ans.append(B[b])
        b+=1
    elif b == len(B):
        ans.append(A[a])
        a+=1
    else:
        if A[a]<B[b]:
            ans.append(A[a])
            a+=1
        else:
            ans.append(B[b])
            b+=1

```

### - 힙 정렬 사용 풀이: 2708ms

```python
# 힙 정렬 2708ms
import sys
input=sys.stdin.readline
import heapq
from heapq import heapify
N,M=map(int,input().split())

L=list(map(int,input().split()))
heapify(L)

L_2=list(map(int,input().split()))

for i in range(M):
    heapq.heappush(L , L_2[i])

for i in range(N+M):
    print(heapq.heappop(L) , end=" ")
```


### - sort() 사용 풀이: 1040ms

```python
# sort 쓰기 1040ms
import sys
input = sys.stdin.readline

n, m = map(int, input().split())

list_a = list(map(int, input().split()))
list_b = list(map(int, input().split()))

c = list_a + list_b
c.sort()

print(' '.join(map(str, c)))
```


## 결론
>… 그냥 내장 sort() 쓰는게 깔끔하고 시간도 훨씬 짧음..;;;
{: .prompt-tip }