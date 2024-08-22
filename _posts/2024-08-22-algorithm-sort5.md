---
title: 백준10814 나이 순 정렬. stable정렬과 unstable정렬
author: jaehyeonee
date: 2024-08-21 12:00:00 +0800
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

## BOJ 10814 나이 순 정렬
문제 링크
[BOJ11728](https://www.acmicpc.net/problem/10814)

>나이가 같으면 먼저 가입한 사람이 앞에 오는 순서로 정렬하는 프로그램을 작성하시오.


이 문제의 주요 쟁점은 위 문장으로 단번에 stable정렬이라는 것을 파악할 수 있다.

**stable 정렬과 unstable 정렬** 에 대해 짧게 설명하자면,



- **stable정렬**은 말 그대로 안정 정렬이다. <br>
입력 받은 값들 중에 __중복되는 값이 있을 경우__, __해당 값의 순서를 그대로 유지한다.__

- **unstable정렬**은 
위와 같은 정렬을 장담하지 않음.

>파이썬은 기본적으로 __stable 정렬__ 을 진행함.
{: .prompt-tip }

### 풀이:

```python
import sys
input = sys.stdin.readline

n = int(input())
arr =[]

for _ in range(n):
    arr.append(input().strip().split())

# data = [[int(age), name] for age, name in arr]
for i in range(n):
    arr[i][0] = int(arr[i][0])

# age를 기준으로 하여 정렬
arr.sort(key = lambda x : x[0])

for i in range(n):
    print(' '.join(map(str, arr[i])))
```