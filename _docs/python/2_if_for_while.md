---
title: if/for/while
category: Python
order: 2
---
## 1. if
- - -
  - if ... elif ... else ... 식의 문법 
  - 조건문, 조건식을 통해서 True, False값이 나오고 True일 때 실행됨
  - 비교 연산자(<,>,== 등)를 이용하는 방법
  - in 연산자를 이용하는 방법 : list, dict ,,,


## 2. for
- - -
  - for ... in ...
  - 반복문
  - range()를 이용하는 방법 : range(len(list)) - list의 크기만큼 반복, 변수에 숫자가 들어감
  - range()를 이용하지 않는 방법 : list - list의 크기만큼 반복, 변수에 list의 요소가 들어감
  - enumerate를 이용하는 방법 : enumerate(list) - list의 크기만큼 반복, lsit의 인덱스와 요소가 들어감
  - list comprehension : 리스트의 []안에 사용해서 요소를 정의하는 방법
  ```python
  list = [i for i in range(10)]
  ```
## 3. while
-----
  - 반복문 
  - 조건문을 만족하는 동안 실행되는 반복문
  - break : 조건문을 빠져나오게 함
  - continue : continue 키워드를 만나면 다음번의 반복을 실행