## 미드 프렌즈 감정분석기 개발(고려대 디지털금융공학석사 과정 기말 프로젝트)
sentimental analysis for 'friends'


## **분석 순서**

0. 목적
1. colab 연결
2. transformer 설치
3. 필요한 라이브러리 가져오기
4. 경로 / max_len 지정
5. 데이터 불러오기
6. 버트 이용을 위한 전처리
7. 데이터 전처리
8. 모델링
9. 학습 및 검증
10. 최종 제출데이타에 대한 예측 수행

## **실행 방법**

- 코드과정마다 텍스트로 설명이 되어 있으니, 코드 파일을 열어보시기 바랍니다.

## **데이터**

- friends_train.json <br>
friends_dev.json <br>
friends_test.json <br>
출처 : http://doraemon.iis.sinica.edu.tw/emotionlines/index.html

- en_data.csv <br>
출처 : https://www.kaggle.com/c/english-sa-competition-dfe610/data

- friends_final.csv <br>
코드를 돌려서 나온 최종값 <br>
이것을 캐글 클래스 경진대회에 올려서 평가함

## **패키지**

- torch
- pandas
- numpy
- RobertaTokenizer 등

## **평가**

- 캐글 클래스 경진대회에 올린 결과 <br>
public 결과는 0.59679(1등) <br>
private 결과는 0.63054(2등) <br>

![frineds_c_title](https://user-images.githubusercontent.com/76524741/103113239-33ee5800-469d-11eb-9890-1cae3d6fcec7.png)
![frineds_public_ldbd](https://user-images.githubusercontent.com/76524741/103113244-3a7ccf80-469d-11eb-8a8e-3134b3c3e7b0.png)
![frineds_private_ldbd](https://user-images.githubusercontent.com/76524741/103113246-3cdf2980-469d-11eb-9f82-bc6e79dc1b1b.png)

## **팁**

1. 데이터 양이 충분치 않다고 생각될 때는 가용가능한 모든 데이터를 사용하면 정확도 향상에 도움이 될 수도 있음 <br>
실제로 train data만을 가지고 돌렸을 때 보다 성능이 좋아짐
2. Large 모델이 Base 모델보다 시간은 더 걸리지만, 정확도 향상에 도움이 됨 <br>
마찬가지로 대소문자 구분하지 않는 것(소문자화 = true)보다 구분하는 것(flase)가 약간이나마 향상 됨
3. 배치사이즈를 크게 하면 속도향상에는 도움이 되나, 메모리가 좋아야 가능함. 256으로 돌려보니, runtime error가 발생하였음. <br>
안전하게 32로 세팅
4. 모델링 시 최초에는 BERT-Large로 진행해봤으나, 정확도 향상에 한계가 존재<br>
RoBERTa 모델을 발견하고 돌리니, 정확도 크게 향상됨 
5. 파라미터 조정(learning rate, epoch, batch size 등) 조정하여 여러번 돌려볼 필요가 있음
