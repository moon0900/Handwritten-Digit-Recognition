# Handwritten-Digit-Recognition
![cover](https://user-images.githubusercontent.com/73999954/230733960-41c24244-60d4-4ca5-b63d-c1b8269c635e.png)


# 0. Introduction

* 2022년 수강한 딥러닝 기초 과목 기말 과제로 수행한 숫자 손글씨 인식 팀 프로젝트
* 최소한의 자원을 사용하여 최대의 학습률과 인식 정확도를 도출하는 것을 목표로 한다.
* 이 프로젝트는 한국인의 숫자 손글씨 특징을 잘 인식할 수 있는 모델을 훈련시키는 것을 목표로 한다.


# 1. Train Dataset
![TrainDataset](https://user-images.githubusercontent.com/73999954/230734083-1f1e5c7b-50b6-4afd-b409-5072ac0be952.png)

모델 훈련을 위한 데이터셋으로 다음의 두 가지 데이터셋을 활용하였다.
* MNIST
  * 공개 서양인 손글씨 데이터셋
  * 총 60,000장
* 한국인 손글씨 데이터셋
  * 30명 정도의 주변인으로부터 직접 수집
  * 총 1,065장
  * with Keras argumentation
    * MNIST에 비해 데이터 수가 적기 때문에 데이터 증강 기법을 적용
    * 이미지를 무작위로 이동, 회전, 확대/축소시켜 증강시킴

# 2. Model
* 다음과 같은 구조의 CNN 모델 사용
![ourCNN](https://user-images.githubusercontent.com/73999954/230733160-2f2f56ca-b384-4e3c-8a69-6ed5c12ff3fb.png)
* 모델의 파라미터는 제시한 목표에 맞도록 자원 사용량과 인식 정확도를 기준으로 실험적으로 선택하였음.
* 총 23,882개의 파라미터 사용.

# 3. Training
* Dropout 적용
* 가중치 매개변수 갱신방법
  * ROMSPROP
    * 기울기를 단순 누적하지 않고 최신 기울기를 더 크게 반영
* 가중치 초기값 설정 방법
  * He Uniform
    * He 정규분포 방식으로 파라미터 초기값 생성
    * 가중치 텐서의 크기에 따라 값을 조절
    
* 한국인 손글씨 데이터셋 훈련 파라미터
  * 배치 크기 5, 에폭 수 60
* MNIST 데이터셋 훈련 파라미터
  * 배치 크기 64, 에폭 수 3
  
# 4. Test
훈련시킨 데이터와 별도의 데이터로 테스트한 결과, 다음의 정확도를 달성.
* mnist 테스트 데이터 - 99%
* 한국인 손글씨 테스트 데이터 - 96.97%

 
