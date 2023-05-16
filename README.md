# Aqu4Men Project

## Overview
Modern individuals are aware of the importance of sufficient hydration, but find it difficult to adhere to.
So we tried to create an environment where you drink water through a smart tumblr with AI.


## Text Mining
Fist of all, we used Web-crawling and Text-mining in order to research the tumblr market.
We collected tumblr purchase reviews and inputed into KoNLPy's OKT which is a morpheme separator.
And then, we created a Word-Cloud and TF-iDF vector.

![TextMining](https://github.com/choiyun9yu/pr.Aqu4Men/blob/main/data/textmining.png)

## Data Modeling
### 1. Logical Model
![ERD](https://github.com/choiyun9yu/pr.Aqu4Men/blob/main/Database/ERD.png)

### 2. Pysical Model
[DCL for Maria DB](https://github.com/choiyun9yu/pr.Aqu4Men/blob/main/Database/DB.SQL)


# 나의 역할 : 머신러닝, 데이터베이스, 서버, 기획
1. 내가 사용한 기술 : Scikit-Learn, KoNLPy, MariaDB, Flask, Arduino-sketch, Final Cut Pro

2. 수행 업무
    - 센싱 데이터 수집, 데이터 전처리, 
    - 회귀 모델링, 군집화 모델링, 분류 모델링,
    - 웹 크롤링 및 텍스트 마이닝,
    - ERD제작 및 데이터베이스 구축,
    - Arduino-Flask연동, Flask-DB연동
    - 프로젝트 기획 및 발표, 영상 촬영 및 편집, NFT제작

# 핵심 개발 내용
1. 가속도 센서를 활용한 유량 예측 '회귀분석'
    - 가속도 센서로 물 마실 때 기우는 컵의 각도를 측정
    - 로드셀 무게 센서로 물 마신 후 줄어든 물의 무게 측정
    - 측정된 값을 Flask 서버를 통해서 데이터베이스에 저장
    - 특성 데이터는 가속도 센서의 측정값, 레이블 데이터는 로드셀 무게 센서 변화값
    - 가속도 센서의 측정값 만으로 마신 물의 양을 측정하는 모델을 개발

2. 물 마시는 각도 변화에 따른 패턴을 비지도학습으로 군집화 하고 '분류예측'
    - 물 마시는 각도 데이터로 덴드로그램 작성
    - 덴드로그램을 바탕으로 3개의 클러스트를 형성
    - 클러스트의 특성을 살피고 패턴을 시각화
    - 특성 데이터는 가속도 센서의 측정값, 레이블 데이터는 군집화 결과값
    - 가속도 센서의 측정값 만으로 어떤 군집에 속해있는지 예측하는 분류모델 개발

3. 경쟁 제품 리뷰 '텍스트마이닝'
    - 웹 크롤링으로 경쟁 제품의 리뷰 데이터 수집
    - 리뷰 데이터를 형태소 분리하여 명사, 동사, 형용사만을 추출
    - 불용어 처리 후 TFiDF를 활용해 의미 있는 키워드를 도출
    - 도출된 키워드를 워드 크라우드를 통해 시각화
    - 우리 제품 지향점 추론

4. 어려웠던 부분
    - 회귀모델 설계 당시에는 액체유량 공식인 M=QxP kg/s을 활용해서   
      텀블러의 입구와 유속만 예측하면 된다고 생각했다. 하지만 가속도 센서로  
      구할 수 있는 값은 물의 속도가 아니라 회전 운동하는 텀블러의 각속도 였다.  
      각속도는 물의 속도가 아닌 단지 물을 마시기 위해 기우는 텀블러의 접선속도이므로  
      위 공식을 사용할 수 없어 어려웠다.
    - 유량을 예측하기 위해서 새로운 공식이 필요했는데 수분을 섭취함에 따라 텀블러 내부  
      물의 양이 줄어 운동 지점이 계속 변하는 것 즉 수위 변수를 측정할 수 없었다.  
      (또한 수위를 알면 역산으로 이미 마신 물의 양을 계산할 수 있는 역설적인 상황이었다.)

5. 아쉬운 부분
    - 머신러닝 회귀분석 오차가 10ml 안팍으로 높은 편이다.
    - 물 마시는 패턴에는 정확도가 높았는데 비즈니스 모델을 찾지 못했다.
    - 프론트엔드 제작이 되지 않아서 백엔드와 연동하지 못한 기능이 있다.
