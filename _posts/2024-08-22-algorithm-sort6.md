---
title: 백준11650/백준11651. 좌표 정렬1,2
author: jaehyeonee
date: 2024-08-21 12:10:00 +0800
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

## BOJ 11650 좌표 정렬
문제 링크
[BOJ11728](https://www.acmicpc.net/problem/11650)

> 람다함수의 key 파라미터에 **튜플**을 사용하면 됨.
`point.sort(key = lambda x: (x[0], x[1]))`
> 

```python
import sys
input = sys.stdin.readline

n = int(input())
point = []

for _ in range(n):
    x, y = map(int,input().split())
    point.append((x,y))

point.sort(key = lambda x: (x[0], x[1]))
for i in range(n):
    print(' '.join(map(str, point[i])))
```

## BOJ 11651 좌표 정렬2
문제 링크
[BOJ11728](https://www.acmicpc.net/problem/11651)

> 람다함수의 key 파라미터에 **튜플**을 사용하면 됨.
> 

```python
import sys
input = sys.stdin.readline

n = int(input())
point = []

for _ in range(n):
    x, y = map(int,input().split())
    point.append((x,y))

point.sort(key = lambda x: (x[1], x[0]))
for i in range(n):
    print(' '.join(map(str, point[i])))
```