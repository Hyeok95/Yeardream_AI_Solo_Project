# Yeardream_AI_Solo_Project
대출자 채무 불이행 예측<br>

* 이 프로젝트는 이어드림 스쿨에서 진행한 프로젝트이며, [AI CONNECT 플랫폼](https://www.aiconnect.kr/main/competition/privateDetail/203/competitionInfo)에서 진행한 대회입니다.

## 1. 대회설명

* 신청 기간 : ~ 1월 26일 08:59 AM
* 대회 기간 : 1월 26일 09:00 AM ~ 2월 8일 12:00 PM
* 참가 대상 : 이어드림 스쿨 수강생으로 제한
* 개인전 (팀 머지 불가)
  * p2p 대부업체의 고객 데이터를 활용한 채무 불이행 여부 예측 과제 수행
  * 본 과제는 실시간 리더보드를 운영하며, 대회 마감 후 추론에 사용한 코드 파일(.ipynb)을 대회 페이지의 '코드 공유' 탭을 통해 제출

## 2. 과제개요

* **대출자 채무 불이행 여부 예측 모델**
수치 영역 | 개방형 문제 | Macro F1 score

* 문제정의
  * p2p 대부업체의 고객 데이터로부터 고객의 채무 불이행 여부에 대한 이진 분류<br>

* 추진배경
  * 핀테크 분야 성장에 따른 금융 분야 AI 활용도 증가
  * 금융 서비스 고객의 분류를 통한 금융 시장 건전성 제고 목표 
  
## 3. 데이터 설명
* 문제설명
  * p2p 대부업체의 고객 데이터를 통한 채무 불이행 여부 예측 과제
  * target 변수가 depvar(dependent variable)라는 이름으로 train.csv에 들어가 있음.
  * 나머지 변수들을 feature로 target 값을 예측하는 모델을 만들어 봄.

* 제출방법
  * 첨부드린 sampe_submission.csv의 answer 값을 추론 값으로 채워서 제출

## 4. 프로젝트 진행 순서
**feature을 조정하고 모델을 설정 한후 파라미터 튜닝을 하려고 하였으나 시간이 오래 걸려, 적합한 모델을 설정하고 파라미터 튜닝을 하고 feature engineering을 실시하였음.** <br>
(그래서 모델 설정 풀이는 이전에 모델 설정과 앙상블 기법 사용, 최적의 파라미터 튜닝을 하여서 생략함.)
1. EDA
2. feature engineering
  * 중복된 컬럼 제거
  * 비슷한 칼럼 한 컬럼으로 label화시키기
  * 이상치 탐지후 정규화
3. 모델 설정 후 학습(lgbm, xgb model 사용)
4. 학습 향상을 위해 앙상블 모델(stacking) 사용
5. permutation Importance를 써서 stacking 모델에 맞는 feature Importance 확인 후 중요도가 0미만인 것 제거 후 다시 feature을 조정 한 후 위 방법 다시 실행.
6. test 데이터에 적용 후 submit 파일로 대입시킨 후 제출

## 5. 사용 스택
### - 개발 환경
  * Google Colab Pro
### - 기술 및 라이브러리
  * Python, numpy, Pandas, Sklearn, Seaborn, Matplotlib, Xgboost, Lightgbm, Catboost,

## 6. 프로젝트 내용 요약
    1. AI Connect 경진대회에서 제공해준 데이터를 이용하여 EDA를 실시함.
    2. EDA 과정에서 feature engineering(중복된 컬럼 제거, 비슷한 컬럼 한 컬럼으로 label화)과 이상치를 탐지한 후 robust scaler를 이용하여 정규화시킴.
    3. 모델 설정 후 Grid Search를 이용하여 파라미터 튜닝시킴 (LightGBM, Xgboost model사용)
    4. 학습향상을 위해 Stacking Ensemble 이용
        - 단일 모델 : 파라미터 튜닝한 LightGBM, Xgboost
        - 최종 모델 : LightGBM
    5. Permutation Importance를 써서 stacking 모델에 맞는 Feature Importance 확인 후 중요도가 0미만인 것 제거 후 다시 feature을 조정 한 후 위 방법 다시 실행.
    6. F1-Score 향상을 위해 threshlod 조정시킴.
    7. test 데이터에 적용 후 submit 파일로 대입시킨 후 제출


  
  
### 주최
중소벤처기업진흥공단

### 주관
마인즈앤컴퍼니
