---
layout: post
title: "Data Mining Lecture #2"
date: 2019-03-14
image: '/assets/img/'
description: 'Lecture 2'
categories:
- Lecture Notes
- Data Mining
---

ML based model development procedure
1. 모델에 사용될 주요 변수 선정
2. 그에 해당하는 데이터 수집
3. 데이터 전처리
4. Training
5. Evaluation

연방론에서 배웟던것처럼 문헌조사를 통해 IV와 DV를 공부하면서 주요 변수 선정.
어떤 변수를 사용할 것인가를 정하면 그 변수를 represent 할수있는 데이터 수집하는 것!

예제: 이탈고객 예측
1. 기존데이터 이용하여 이탈가능성높은고객과 계약갱신가능성 높은 고객들의 프로파일 파악. (DB에서 고객군 분류, 고객군의 특징 파악.)
2. 각 고객이 이탈고객일지 갱신고객일지 파악. (이탈을 판별할 수 있는 모델 개발)

예제: 수익최대화를 위한 타겟마케팅
1. 프로모션 실시할 경우 반응할 가능성 높은 고객 파악 (고객 분류 모델 개발)
2. 모델별 타겟마케팅에 따른 기댓값 계산, 비교, 및 모델 선정 (기댓값 계산(투자대비 효과))
3. 예산 한도 내에서 타겟마케팅 대상자 선정(기댓값 계산 및 상위 순위/최대 profit 기준 선별)

#### 데이터 전처리와 데이터 정제
변수선택
- 변수 간 상관관계가 크면 둘중 하나의 변수만 포함시키는게 바람직.
- 너무 많은 변수는 과적합으로 이어짐.

데이터 통계분석
- 통계 요약을 보고 outlier 제거 (can be solved by Boxplot IQR(outlier<Q1-1.5*IQR&&Q3+1.5*IQR < outlier) )
- 상관분석을 통해 다중공선성과 같은 문제 해결.

아웃라이어
- 평균적으로 std의 3배가 넘는 범위의 데이터

missing Data
- 적으면 삭제 후 분석
- 변수의 중요도를 측정하여 예측에 미치는 영향력이 미미하면 변수 삭제

정규화 / 표준화
- min-max normalization
- z-score normalization (for continuous)
- decimal scaling

Evaluation
- 개발된 모델이 비즈니스 목적을 만족시키는가?
- 비즈니스 이슈가 고려되지못한게 있는가?
- applicability?
- Confusion Matrix

#### Data Understanding
- null data check
- strange minimum or maximum?
- strange mean or large differences between mean and median?
- large skew or excess kurtosis? (if algorithm is assuming normal distribution)
- gaps in distributions? (Bi-modal or multi-modal 산봉우리가 몇개인가)

#### Data Preparation
1. Variable Cleansing
  - For categorical variable, examine frequency count and identify unusualness or infrequency.
  - For continuous variable, follow outlier handling process.
  - 아웃라이어 제거는 알고리즘에 따라 다름. Decision Tree는 안해줘도됨.
  - for Missing values,
    - Row deletion / Col Deletion
    - Imputation with constant (U for missing for categorical data)
    - Mean/Median Imputation
    - Distribution imputation
2. Feature Creation
Features are new variables to add to data that are created from one or more existing variables already in the data: derived variables or derived attributes.
(각 X별 distribution을 보고 맞는 조치를 취하도록.)
  - Data Skewness
    - Positive skew lead to high bias(underfit) for Linear regression, K-NN, K-Means
    - Decision Tree unaffected by skewness
    - To fix, log transform for positive skewness, power transform for negative.
  - normalization
    - magnitudes of variables can also bias the models for K-NN
      - Linear Regression is affected by the skewness, not magnitudes.
    - z-score for normally distributed data.
  - Nominal Variable Transformation (One Hot)
  - Binning Continuous Variables (강의노트 참조)
3. Variable Selection
  - Remove irrelevant variables
  - remove redundant variables (0.9 threshold rule of thumb)

3.1 Curse of Dimensionality
  - sample data size 정하기
  - Dimensionality Reduction : Feature selection, PCA(Feature Extraction)

4. Sampling
  - if input size is large, 100 observations per input.
  - Cross-Validation
  - Bootstrapping (Samples the data with replacement)
  - Stratified Sampling (balances counts based on one or more variables)
