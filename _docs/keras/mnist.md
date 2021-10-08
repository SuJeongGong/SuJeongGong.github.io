---
title: mnist
category: Keras
order: 1
---
## 1. 데이터 가져오기 
- - -
  keras에서 제공해주는 데이터 셋을 가져옵니다.
  ```python
  mnist = tf.keras.datasets.mnist
  (train_images, train_labels), (test_images, test_labels) = mnist.load_data()
  ```
   
## 2. 값 설정하기
- - -
       
  이미지의 채널 값, 가로, 세로, 정답의 갯수 등을 설정해놓습니다.
  ```python
  IMG_CHANNEL = 1    # 흑백이라서 1, 컬러는 3
  EPOCHS = 5
  IMG_HEIGHT = train_images.shape[1]
  IMG_WIDTH = train_images.shape[2]
  labels_count = len(set(train_labels))   # set으로 중복제거해서 갯수 세기
  ```

## 3. 전처리 
- - - 
  이미지의 값이 [0, 255] 범위인데 이 값은 신경망에 이상적이지 않아서 **[0, 1] 범위의 값으로 변환**
  ```python
  train_images = train_images.astype(np.float32) / 255.
  test_images = test_images.astype(np.float32) / 255.
  ```

## 4. 모델 구성
- - -
  모델은 Sequential 모델을 사용
  ```python
  model = tf.keras.models.Sequential([
      tf.keras.layers.experimental.preprocessing.Rescaling(1./255, input_shape=(IMG_HEIGHT, IMG_WIDTH, IMG_CHANNEL)),
      tf.keras.layers.Conv2D(filters=64, kernel_size=1, activation=tf.nn.relu, padding='same'),
      tf.keras.layers.Flatten(),
      tf.keras.layers.Dense(128, activation=tf.nn.relu),
      tf.keras.layers.Dense(labels_count, activation=tf.nn.softmax)
  ])

  tf.keras.layers.experimental.preprocessing.Rescaling(1./255, input_shape=(IMG_HEIGHT, IMG_WIDTH, IMG_CHANNEL))
  ```
  이 코드문은 3번 전처리를 하는 부분과 같은 내용이다.  
  데이터에 직접 전처리를 해도 되고, 안했다면 모델 틍에 넣어주는 것도 또 다른 방법이 될 수 있다.   

## 5. 모델 컴파일
- - -
  ```python
  model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])
  ```

## 6. 모델 훈련
- - -
  ```python
  model.fit(train_images, train_labels, epochs=EPOCHS)
  ```

## 7. 정확도 평가
- - -
  ```python
  test_loss, test_acc = model.evaluate(test_images, test_labels)
  print('test_loss:', test_loss)
  print('test_acc:', test_acc)
  ```