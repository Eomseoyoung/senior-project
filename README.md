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
![졸작 블럭도](https://user-images.githubusercontent.com/105179675/175463518-7d1a1383-cbfd-497b-b8b6-a5cb440ff15d.PNG)





## 5. 얼굴 인식 진행사항
***
모델을 cnn으로 구현 중 교수님께 조언을 받고 teachable machine으로 바꾸어 모델 추출 완료 후 python에서 opencv를 써서 사용하고 현재 웹 진행 중
하지만 각도가 달라지거나 옷이 달라져도 정확도가 떨어짐 -> 더 많은 데이터 확보로 모델 추출 재시도
![image](https://user-images.githubusercontent.com/105179675/168030106-62e1658a-5461-424e-9a90-37eeadda5b9e.png)

**얼굴인식률이 낮아 dlib을 사용 중**





## 6. 웹서버설계
***
**자바스프링을 사용**

(1) 로그인 이후 스트리밍을 받을 수 있는 창(초안)
![웹구상_1](https://user-images.githubusercontent.com/105179675/174916545-ec5db82e-a225-428c-8054-284f316cee17.png)

(2) 회원가입 (초안)
![웹구상_2](https://user-images.githubusercontent.com/105179675/174916552-a94a1720-d939-4b8c-9da8-0383e9f8c3d8.png)


## 7. 스트리밍 진행사항
***

**VLC 를 이용하여 스트리밍 서버를 만들어서 html로 만든 사이트에 영상 수신**

1. 스트리밍 ip주소를 따옴.
2. 그 주소를 포트포워딩함
3. 포트포워딩한 주소를 프로토콜형식으로 변환

(vlc로 확인)
![스트리밍_1](https://user-images.githubusercontent.com/105179675/174916511-ac809b8e-71c4-41eb-9dbb-21794eca96ca.png)
(스트리밍 창 )
![스트리밍_2](https://user-images.githubusercontent.com/105179675/174917593-49c03de4-e35e-40be-9a06-7ca9cc094a79.png)





## 8. 참고한 링크
***

[스트리밍](https://m.post.naver.com/viewer/postView.nhn?volumeNo=29553682&memberNo=2534901&vType=VERTICAL)

[얼굴인식_dlib](https://yunwoong.tistory.com/84)

[dlib_설치_anaconda](https://blog.naver.com/PostView.nhn?blogId=os2dr&logNo=221818707061&categoryNo=0&parentCategoryNo=0&viewDate=&currentPage=1&postListTopCurrentPage=1&from=postView)
