###### 얼굴인식 자동출석 프로그램


# 1. 작품의 필요성
*** 
코로나 시대의 비대면 수업이 많아진 오늘날 원격수업을 듣는 학생들의 집중력 저하 및 얼굴확인이 불가능하므로 대리출석이나 화면을 꺼놓는 상황이 발생되어 그 문제를 사전에 방지하여 선생님의 편의와 학생들의 수업능률 향상을 위하여 제작하게 됨


# 2. 작품 목표
***
여러명의 얼굴은 인식하고 웹에 저장 후 얼굴인식 확률을 95퍼 이상으로 만듦


# 3. 작품 세부내용
***
1. 수업 입장 시 얼굴 인식된 사람만 입장이 가능
2. 미출석 인원이 있을 경우 교수님께 알림
3. 수업 중 고개를 숙이거나 눈이 감겨 있는 행동이 5분이상 지속시 알림
4. 데이터베이스를 통해 출석확인과 동시에 점수 부여


# 4. 블록도
***
![블록도](https://user-images.githubusercontent.com/105179675/168029591-fee5c1a0-b585-4f60-bbb4-1cfe7b46bc28.PNG)


# 5. 진행사항
***
모델을 cnn으로 구현 중 교수님께 조언을 받고 teachable machine으로 바꾸어 모델 추출 완료 후 python에서 opencv를 써서 사용하고 현재 웹 진행 중
하지만 각도가 달라지거나 옷이 달라져도 정확도가 떨어짐 -> 더 많은 데이터 확보로 모델 추출 재시도
![image](https://user-images.githubusercontent.com/105179675/168030106-62e1658a-5461-424e-9a90-37eeadda5b9e.png)


# 6. 사용한 소스코드
***

<pre>
<code>
import tensorflow.keras
import numpy as np
import cv2

model = tensorflow.keras.models.load_model('keras_model.h5')

cap = cv2.VideoCapture(0)

size = (224, 224)

classes = ['minsu', 'donghun', 'kihwan']

while cap.isOpened():
    ret, img = cap.read()
    if not ret:
        break

    h, w, _ = img.shape
    cx = h / 2
    img = img[:, 200:200+img.shape[0]]
    img = cv2.flip(img, 1)

    img_input = cv2.resize(img, size)
    img_input = cv2.cvtColor(img_input, cv2.COLOR_BGR2RGB)
    img_input = (img_input.astype(np.float32) / 127.0) - 1
    img_input = np.expand_dims(img_input, axis=0)

    prediction = model.predict(img_input)
    idx = np.argmax(prediction)

    cv2.putText(img, text=classes[idx], org=(10, 30), fontFace=cv2.FONT_HERSHEY_SIMPLEX, fontScale=0.8, color=(255, 255, 255), thickness=2)

    cv2.imshow('result', img)
    if cv2.waitKey(1) == ord('q'):
        break
</code>
<pre>



