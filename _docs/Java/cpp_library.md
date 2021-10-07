---
title: C++ 라이브러리 연동 (JNI)
category:  Java
order: 1
---

업무상 jsp 프로젝트에서 C++ 라이브러리를 사용해야 하는 일이,,,생겼습니다...
그래서 java와 C++라이브러리를 연동하는 방법을 찾아서 해봤습니다.
처음 해보는 일이라 굉장히 헤맸지만,,, 그래서 까먹지 않으려고 정리해보겠습니다.
기억을 진행하면서 기록한 것이 아니라 명렁어나 코드는 약간 다를 수 있습니다.

먼저 "JNI"라는 라이브러리를 이용해서 연동할 겁니다.
특징으로는 java는 원래 os에 종속되지 않지만, 이걸 사용하면 os 종속성이 생기게 됩니다.

작업환경
- java 1.8
- window

대략적인 순서는 아래와 같습니다.
1. java 코드 작성
2. 작성한 java코드로 c++의 헤더파일 만들기
3. 만들어진 헤더파일을 구현하는 c++ 코드 작성


1. java 코드 작성
먼저 java에서 c++라이브러리와 연동할 클래스 파일을 만들어 주어야 합니다.
그리고 그 안에 

        static {
        		System.loadLibrary("libfota_10061727");
        	}

이렇게 .dll 파일 이름을 넣어주어서 C++을 연결 시켜주고,

        public native String run(String a, int b);

이런식으로 c++에서 작성 되어있는 (혹은 작성할) 메서드를 구현하지 않고 선언만 해놓습니다.
여기서 중요한 점은 "native"라는 키워드를 메서드에 붙여서 native 메서드로 만들어야합니다.
또 여기의 메서드 이름은 실제 C++에 정의된 메서드 이름과 달라도 됩니다.

2. 작성한 java코드로 c++의 헤더파일 만들기
이렇게 클래스를 작성했다면 .java라고 끝나는 파일을 .class 파일로 만들고 .class파일을 .h 파일로 만들어 줄 겁니다.
다른 방법도 있다고 하는데 저는 cmd를 이용해서 진행 했습니다.
cmd에서 .java파일이 있는 위치로 이동해

        javac test.java

명령어를 입력해 .java -> .class로 바꾼뒤
위치를 다시 패키지가 있는 위치로 이동해 패키지명이 com.test.www 였다면

        javah com.test.www.[java파일명]

명령어를 실행해서 .h파일을 만들어 냅니다.

3. 만들어진 헤더파일을 구현하는 c++ 코드 작성
이렇게 만들어진 헤더파일을 가지고 C++코드를 작성하면됩니다.
저는 C++를 몰라서 조금 힘들었습니다,,ㅠㅠ

참고할 점
- .h에는 메서드 매개변수를 작성하는 부분에 변수명을 따로 넣지 않는다는 점
- 하지만 .cpp에서는 메서드 매개변수를 작성하는 부분에 변수명을 넣어야 한다는 점
- 매개변수 타입이 string은 jstring과 같이 앞에 j가 붙는 원래 C++에서는 사용되지 않는 타입이라 변환해서 사용해야 한다는 점
    - jstring -> string 변환

            const char *temp = env->GetStringUTFChars([jstring 변수명], NULL);	//TEST_COMP
	        std::string [string 변수명] = std::string(temp);

    - jint -> int 변환

            int TEST_SB_TYPE = (int)SB_TYPE;

- c++에서 printf문으로 출력한 것은 java콘솔에서 찍히지 않는다. 확인하려면 txt파일로 내보내서 확인하는 것도 좋은 방법

        FILE *wfp = NULL;
        wfp = fopen("경로\\time.txt", "w");   // 열기
        if (wfp == NULL)
        {
            printf("write error");
            exit(4);
        }
        fprintf(wfp, "COMP  \t\t: %s\n", TEST_COMP.c_str());
        fclose(wfp);   // 닫기
        
    - 경로를 구분할 때에는 \가 아니라 \\이렇게 두개를 붙여서 구분!
- C++ -> java String 리턴시 한글은 깨지는 오류가 있었는데 영문만 리턴할거라 따로 해결하지 않고 사용했습니다. 찾아보셔야할것같아요!
- java -> C++ String도 한글이 깨지는 경우가 있다고 하던데 저는 따로 깨지지 않아서 해결하지 않았습니다. 필요시 검색해보세요


참고 : https://sungcheol-kim.gitbook.io/jni-tutorial/ 