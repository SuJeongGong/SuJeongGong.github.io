---
title: Layer의 종류
category: Keras
order: 2
---
1. Dense Layer
   
   다층 퍼센트론 신경망, 입력과 출력을 모두 연결

   각 연결선은 가중치를 포함하고 있는데, 연결 강도를 의미
   
   가중치는 높을수록 해당 입력 뉴런이 출력 뉴런에 미치는 영향이 크고, 낮을수록 미치는 영향이 작다.


2. Convolution Layer
   
   Convolution 신경망, 이미지 특성이 고려된 신경망, 다층 퍼셉트론 신경망과 유사함
   
   주요 레이어 : Conv2D, Maxpooling, Flatten


3. Max Pooling Layer
   
   Conlvolution Layer의 출력 이미지에서 주요 값만 뽑아 출력 영상을 만듬
   

4. Flatten Layer
   
   Convolution 와 Max Pooling 를 반복적으로 거치면 주요 특징만 추출, 전결합층에 전탈되어 학습됌   
   
   전 결합층에 전달하기 위해서 1차원 자료로 바꿔줄때 사용되는 레이어
   

5. LSTM Layer
   
   ??! 이건 처음들어봐!!!



*참고*

https://ssongnote.tistory.com/13