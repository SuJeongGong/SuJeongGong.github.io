---
title: 자바 웹 프로젝트 window -> linux 배포
category: Java
order: 2
---

jsp 프로젝트나 spring 프로젝트를 완성하면 배포해서 리눅스 서버에 배포하는 일이 종종 있는데 순서와 방법에 대해서 적으려고 합니다.  

순서
1. 기존에 있던 tomcat 복사  
2. port 열기
3. server.xml 파일 수정
4. war파일 서버로 옮기기
5. tomcat 서비스 복사하기 
6. 서비스 실행  



## 1. 기존에 있던 tomcat 복사  
*****************
  1. 기존에 있던 tomcat 폴더를 복사합니다.
  2. 그 안에 webapps 폴더에서 ROOT 폴더와 ROOT.war파일을 삭제합니다.
  - 체크해야할 부분 복사한 폴더의 권한을 체크합니다



## 2. port 열기
* * *
  1. port를 열기 전에 어떤 port가 열려있는지 확인합니다. 
  ```
  firewall-cmd --list-all
  ```
  2. 사용하지 않는 port 번호 중에서 원하는 port 번호를 개방합니다.
  ```
  firewall-cmd --zone=public --permanent --add-port=[원하는 번호]/tcp
  ```
  - 열었던 port를 삭제하고 싶다면
  ```
  firewall-cmd --zone=public --permanent --remove-port=[삭제한 번호]/tcp
  ```
  3. 방화벽을 재가동 합니다.
  ```
  firewall-cmd --reload
  ```

## 3. server.xml 파일 수정
- - -  
  - context 태그에 실행할 war파일 변경
  - port번호 변경 ( 개방한 port 번호로 )
  - tomcat 폴더 이름 변경


## 4. war파일 서버로 옮기기
- - -  
  - 이클립스를 통해서 war파일을 만들 때에는 서버에 설치되어있는 tomcat 버전에 맞춰서 내보기
  - 내보내는 위치 : 톰캣폴더/webapps/


## 5. tomcat 서비스 복사하기 
- - -  
  1. 기존에 있던 tomcat 서비스를 복사
  2. tomcat 폴더명 변경하기


## 6. 서비스 실행  


- 추가로 알아두면 좋을 내용
  - 이렇게 한 뒤에 수정한 파일 다시 배포하고 싶다면  
  : 서비스 멈추고 war파일 -> war파일 풀린것 둘 다 삭제 (위치 : webapps) -> 서비스 실행