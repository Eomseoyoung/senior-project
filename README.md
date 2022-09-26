# _얼굴인식 자동출석 프로그램_


## 1. 작품의 필요성
*** 
코로나 시대의 비대면 수업이 많아진 오늘날 원격수업을 듣는 학생들의 집중력 저하 및 얼굴확인이 불가능하므로 대리출석이나 화면을 꺼놓는 상황이 발생되어 그 문제를 사전에 방지하여 선생님의 편의와 학생들의 수업능률 향상을 위하여 제작하게 됨


## 2. 작품 목표
***
여러명의 얼굴은 인식하고 웹에 저장 후 얼굴인식 확률을 95퍼 이상으로 만듦


## 3. 작품 세부내용
***
1. 수업 입장 시 얼굴 인식된 사람만 입장이 가능
2. 미출석 인원이 있을 경우 교수님께 알림
3. 수업 중 고개를 숙이거나 눈이 감겨 있는 행동이 5분이상 지속시 알림
4. 데이터베이스를 통해 출석확인과 동시에 점수 부여


## 4. 블록도
***
![졸작블럭도](https://user-images.githubusercontent.com/105179675/175839077-d8212a2b-5a7a-4df4-93fe-9db5d68848c6.PNG)





## 5. 얼굴인식 설계
***
### 1. teachable machine model 사용 얼굴 인식 설계 (실패)

(1) 모델을 cnn으로 구현 
(2) teachable machine을 사용해 model(.h5) 추출
(3) python에서 opencv 라이브러리를 사용해 실행


![image](https://user-images.githubusercontent.com/105179675/168030106-62e1658a-5461-424e-9a90-37eeadda5b9e.png)

문제점1) 많은 데이터를 가져도 얼굴인식률이 낮음
문제점2) cnn으로 구성되어있어서 얼굴 분류만 가능
문제점3) 각도가 달라지거나 옷이 달라져도 정확도가 떨어짐





***

### 2. dlib 얼굴 인식 설계 (진행중)

1) c++ 라이브러리라서 anaconda를 사용해 python에 사용 가능하게 설치
2) 얼굴인식을 위해 얼굴 데이터 수집 

![image](https://user-images.githubusercontent.com/105179675/192308500-df332076-1901-4b9d-9c54-aa96d37fba9f.png)

![image](https://user-images.githubusercontent.com/105179675/192308660-a2ec2250-eeee-479e-b9c0-375e7fb9fc5d.png)


3) 얼굴인식 성공


## 6. 웹서버 설계 (진행중)
***
(1) 자바 스프링 사용
(2) 회원가입하는 창 설계
(3) 로그인 이후 스트리밍을 받을 수 있는 창 설계

(1) 로그인 이후 스트리밍을 받을 수 있는 창(초안)
![웹구상_1](https://user-images.githubusercontent.com/105179675/174916545-ec5db82e-a225-428c-8054-284f316cee17.png)

(2) 회원가입 (초안)
![웹구상_2](https://user-images.githubusercontent.com/105179675/174916552-a94a1720-d939-4b8c-9da8-0383e9f8c3d8.png)


## 7. 스트리밍 설계
***

(1) 스트리밍 서버를 만듦.
(2) VLC 사용 
(3) 스트리밍 ip주소를 따옴.
(4) 그 주소를 포트포워딩함
(5) 포트포워딩한 주소를 프로토콜형식으로 변환

(vlc로 확인)
![스트리밍_1](https://user-images.githubusercontent.com/105179675/174916511-ac809b8e-71c4-41eb-9dbb-21794eca96ca.png)
(스트리밍 창 )
![스트리밍_2](https://user-images.githubusercontent.com/105179675/174917593-49c03de4-e35e-40be-9a06-7ca9cc094a79.png)





## 8. 참고한 링크
***

[스트리밍](https://m.post.naver.com/viewer/postView.nhn?volumeNo=29553682&memberNo=2534901&vType=VERTICAL)

[얼굴인식_dlib](https://yunwoong.tistory.com/84)

[dlib_설치_anaconda](https://blog.naver.com/PostView.nhn?blogId=os2dr&logNo=221818707061&categoryNo=0&parentCategoryNo=0&viewDate=&currentPage=1&postListTopCurrentPage=1&from=postView)
