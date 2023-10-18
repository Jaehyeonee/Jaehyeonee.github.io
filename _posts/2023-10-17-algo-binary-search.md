---
title: Algorithm. 이진탐색(Binary Search)
author: jaehyeonee
date: 2023-10-05 15:35:00 +0800
categories: [Study, Algorithm]
tags: [Algorithm]
pin: true
math: true
mermaid: true
# image:
#   path: 
#   lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
#   alt: Responsive rendering 
---


# 이진 탐색 Binary Search
>반으로 쪼개면서 탐색하기

이진탐색은 배열 내부의 데이터가 정렬되어 있어야만 사용할 수 있는 알고리즘이다.
데이터가 랜덤일 때는 사용할 수 없지만, 이미 정렬되어 있다면 매우 빠르게 데이터를 찾을 수 있다.

>원하는 조건을 만족하는 가장 알맞은 값 찾기 = 최적화 문제 = 이진 탐색
{: .prompt-tip }

### 어떤 문제가 이진 탐색 문제일까?
1. 반복해서 최선의 경우를 찾아 낼 때
2. 내부 데이터가 정렬되어 있을 때
3. 범위를 좁혀 원하는 조건을 만족하는 최적값을 찾을 때

이진 탐색의 가장 큰 아이디어는 탐색의 범위를 절반씩 좁혀간다는 특징이다.

__이미 정렬된 10개의 데이터 중에서 값이 4인 원소를 찾는다고 가정하자.__
<br>
배열의 시작점 [0], 끝점 [9], 중간점은 인덱스[4]이다.
인덱스 4의 위치를 보면 값이 `8` 이다. 찾고자 하는 수 `4` 보다 큰 수 이므로, `8` 뒤에는 버린다. <br>

1.
`0` `2` `4` `6` `8` `10` `12` `14` `16` `19`
  
2.
`0` `2` `4` `6` 
끝점 인덱스 [3]의 중간인 [1]을 보면 `2` 로 `4` 보다 작다. 따라서 왼쪽은 버린다.

3.
`4` `6` 
끝점[1] 중간인 인덱스[0]을 보면 찾고자 하는 값 `4` 를 찾을 수 있다.



<br>
전체 데이터의 개수는 10개지만, 이진 탐색을 이용하면 총 3번의 탐색으로 원소를 찾을 수 있다.
이진 탐색은 한 번 확인할 때마다 탐색해야 할 데이터 수가 절반씩 줄어든다. <br>
따라서, 이진 탐색 알고리즘의 시간 복잡도는  __O(logN)__ 이다.

## 코딩 테스트에서의 이진 탐색
```python
def binary_search(array, target, start, end):
  while(start <= end):
    mid = (start+end)	// 2
    
    if array[mid] == target:
      return mid
    # end = mid - 1
    elif array[mid] > target:
      return binary_search(array, target, start, mid - 1)
    else:
		# start = mid + 1
			binary_search(array, target, mid+1 , end)
```

### 트리 자료구조

트리 자료구조는 노드와 노드의 연결로 표현한다. 노드는 정보의 단위로서 어떠한 정보를 가지고 있는 개체로 이해할 수 있다. 트리 자료구조는 그래프 자료구조의 일종으로 데이터베이스 시스템이나 파일 시스템과 같은 곳에서 많은 양의 데이터를 관리하기 위한 목적으로 사용된다.

#### 트리 자료 구조의 특징
> 1.트리는 부모 노드와 자식노드의 관계로 표현
> 
> 2.트리의 최상단 = 루트 노드
> 
> 3.트리의 최하단 = 단말 노드
> 
> 4.트리에서 일부를 떼어내도 트리구조이며, 이를 `서브 트리`라고 한다
> 
> 5.트리는 파일 시스템과 같이 `계층적이고 정렬된 데이터`를 다루기 적합



>데이터를 트리 자료구조로 저장해서 이진탐색과 같은 탐색 기법을 이용해 빠르게 탐색이 가능하다!
{: .prompt-tip }

### 이진 탐색 트리 
![IMG_41A986E5616C-1](https://github.com/Jaehyeonee/codingTest-study/assets/92504386/eba34ad7-ef1f-46fa-94d9-ae82b9996480)
1. 부모 노드보다 왼쪽 자식 노드가 작다.
2. 부모 노드보다 오른쪽 자식 노드가 크다.


이진 탐색 트리에 데이터를 넣고 빼는 방법은 알고리즘보다는 자료구조에 가깝다. 이진 탐색 트리 자료구조를 구현하는 문제는 출제 빈도가 낮다. 이미 이진 탐색 트리가 구현되어 있다고 가정하고, 이진탐색트리에서 데이터를 조회하는 과정을 보자!
  
![IMG_576C4AC8717D-1](https://github.com/Jaehyeonee/codingTest-study/assets/92504386/e012aac1-a505-4f5f-8d26-95f3a077d973)

__이진 탐색 트리의 조건에 맞게 설정된 위와 같은 트리가 있을 때, 타겟 원소 `37` 을 찾아보자.__
1. 부모 노드(=mid)와 타겟 값을 비교한다.<br>
`37` 에 비해 부모 노드가 작으므로 부모 노드를 기준으로 왼쪽은 전부 버리고, 오른쪽 서브트리만 본다.

2. 서브 트리의 부모 노드(=mid) `48` 이, 타겟 값보다 크다. 따라서 왼쪽만 탐색한다.
3. 타겟값을 찾았다!


## 💭
이진 탐색 문제는 입력 데이터가 많거나, 탐색 범위가 매우 넓은 편이다. 데이터의 개수가 1,000만개를 넘어가거나 탐색범위가 1,000억 이상이라면! __이진 탐색을 의심해보자__

>입력데이터가 많은 문제에 input() 함수를 사용하면 동작 속도가 느려 시간초과가 된다. 따라서 입력 데이터가 많은 문제는 `sys라이브러리`의 `readline()`함수를 이용하자!
{: .prompt-warning}

  ```python
  import sys

  input_data = sys.readline().rstrip()

  ```