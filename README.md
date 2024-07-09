# Regression_model
- 주제 : Kaggle 데이터 활용한 예측 모델 구축 

## 분석 내용 요약
  
  - 콘크리트 생성에 필요한 구성요소 조건에 관한 데이터를 기반으로 콘크리트 강도를 예측하는 모델을 개발함으로써 부실 공사를 예방하고, 구조물 수명을 연장하며 유지 보수 비용을 절감하여 건설 프로젝트의 안정성과 경제성을 동시에 향상시키고자 하였습니다.
  - kaggle에서 제공하는 데이터를 활용하였고, 회귀 모델 대회를 택하여, 상위 10% 이내에 진입하는 것을 목표로 프로젝트를 수행하였고, 결과적으로 프로젝트 마무리 시기, RMSE 12.27435점으로 ranke 55등인 상위 7%에 도달하였습니다.
    
      - 배경 : 콘크리트 강도 예측 모델의 개발은 건설 산업에서 안정성과 경제성을 확보하는 필수적인 과제이며, 부실 건설물 문제에 대응하기 위해 시급함을 파악함.
      - 프로젝트 기간 : 2024년 4월 11일 ~ 2024년 4월 26일
      - skill & Tool : python, jupyter, google colaboratory, notion
      - 데이터 수집 방식 : kaggle 사이즈 제공 데이터 활
      - 데이터 분석 방식 : 피처 특성에 따른 데이터 인코딩 진행 후, 머신러닝 모델 적
        
## 분석 결과

- 사전적 정보에 의하면, CementComponent, WaterComponent 요소가 콘크리트 강도와 밀접한 관련이 있음. 그러나 EDA 결과, WaterComponent 요소를 제거하였을 때, 모델 성능이 더욱 향상됨.
    - CementComponent, WaterComponent는 개별적인 피처로 파악하는 것이 아닌, **CementComponent와 WaterComponent의 구성 비율 정도로 강도를 예측하는 것이 필요**함.
- 콘크리트를 구성하는 요소들 역시 중요하나, **콘크리트를 건조시키는 ‘일수’가 강도를 높이는데 중요한 요소**임을 파악할 수 있음.

- 최종 활용 모델
    - AutoML -> GradientBoostingRegressor()
    - optuna -> 하이퍼파라미터탐색 -> GradientBoostingRegressor() 회귀 모델 생성 -> 교차 검증을 통한 평가 -> 최적화 -> 모델 훈련 -> 모델 평가
    - kaggle 제출 결과
        - private score: 12.27435(RMSE)
