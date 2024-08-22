---
title: 백준2750, 2751. 수 정렬하기 알고리즘
author: jaehyeonee
date: 2024-08-21 11:30:00 +0800
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

## BOJ 2750 수 정렬하기1

문제 링크
[BOJ11728](https://www.acmicpc.net/problem/2750)


```python
import sys
input = sys.stdin.readline

n = int(input())

num = list(int(input()) for _ in range(n))
num.sort()

for i in range(n):
    print(num[i])
```

## BOJ 2751 수 정렬하기 2  

문제 링크
[BOJ11728](https://www.acmicpc.net/problem/2751)

merge sort 합병정렬을 이용해 풀이<br>
```→ O(nlogn)의 시간복잡도를 가진다.```

```python
import sys
input = sys.stdin.readline

n = int(input())

num = list(int(input()) for _ in range(n))

def merge_sort(num):
    if len(num) <= 1:
        return num
    mid = len(num) // 2
    left = num[:mid]
    right = num[mid:]

    left = merge_sort(left)
    right = merge_sort(right)

    return merge(left, right)

def merge(left, right):
    result=[]
    i, j = 0,0

    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1

    result += left[i:]
    result += right[j:]

    return result

ans = merge_sort(num)
for i in range(n):
    print(ans[i])

```
