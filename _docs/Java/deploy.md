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
- - -  
    1. 기존에 있던 tomcat 폴더를 복사합니다.
    2. 그 안에 webapps 폴더에서 ROOT 폴더와 ROOT.war파일을 삭제합니다.
    - 체크해야할 부분 복사한 폴더의 권한을 체크합니다



## 2. port 열기
- - -  
  1. port를 열기 전에 어떤 port가 열려있는지 확인합니다. 
  `
  firewall-cmd --list-all
  `
  2. 사용하지 않는 port 번호 중에서 원하는 port 번호를 개방합니다.
  `
  firewall-cmd --zone=public --permanent --add-port=[원하는 번호]/tcp
  `
  - 열었던 port를 삭제하고 싶다면
  `
  firewall-cmd --zone=public --permanent --remove-port=[삭제한 번호]/tcp
  `
  3. 방화벽을 재가동 합니다.
  `
  firewall-cmd --reload
  `



## 3. server.xml 파일 수정
- - -  



## 4. war파일 서버로 옮기기
- - -  



## 5. tomcat 서비스 복사하기 
- - -  



## 6. 서비스 실행  
- - -  

