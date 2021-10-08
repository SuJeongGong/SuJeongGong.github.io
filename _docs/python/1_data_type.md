---
title: data type
category: Python
order: 1
---
## 1. list
- - -
- 배열과 비슷한 성질이 있는 데이터 타입, 다른점은 각 요소의 데이터 타입이 달라도 된다.
- 특징
  - 한 리스트 안의 각 요소가 데이터 타입이 달라도 된다. 
  - -(마이너스)인덱스 : 리스트의 마지막 요소의 인덱스를 -1, 그 전의 -2 ,,, 이런식으로 마이너스 인덱스가 있다.
  - 슬라이싱 : :(콜론)을 이용한 슬라이싱 기능이 있다.
  ```python
  list_name[start_index : end_index] 
  ```
  list_name이라는 리스트가 있다고 할 때,list_name의 start_index부터 end_index -1까지를 리스트로 반환한다.  
  ```python                    
  list_name = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
  list_name_2 = list_name[1:5]
  print(list_name_2)
  # 결과 
  [2, 3, 4, 5]
  ```


## 2. tuple
- - -
  - list와 거의 비슷한 데이터 타입, 다른점은 값을 변경 할 수 없다는 점이다.  


## 3. dictionary
- - -  
  - 키와 값이 한 쌍으로 저장된 데이터 타입이다.
    