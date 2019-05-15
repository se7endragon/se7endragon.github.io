---
layout: post
title: "Data Mining Lecture"
date: 2019-03-28
image: '/assets/img/'
description: 'Lecture 4'
categories:
- Lecture Notes
- Data Mining
---

# 데이터에 대한 모델 적합화

Parametric Modeling
- 일부 수치형 파라미터를 지정하지 않고 모델 구조만 만들어 놓은 상태에서 데이터 세트에 fit.
- 예를 들어 각종 regression들은 predefined된 모양의 수식이 있기때문에 parametric modeling.
- 즉 fit 시킬때 최적의 Parameter을 찾는것.

Curse of Dimensionality 해결법
##### Dimensionality Reduction
- missing value 90% 이상이면 remove col
- skewness 0.1보다 작으면 remove col
- std 0.1보다 작으면 remove col

### 선형판별식 (Linear Classifier Function)
판별분석에서는 observation들이 속하는 class label을 구별할수있는 decision boundary를 나누는 것.
- 단순히 어디 class에 속할것이다에서 멈추는게 아니라 몇% 확률로 속할것이다 라는걸 알 수 있으면 의사결정에 도움이 더 됨.
- class에 속할 확률을 추정할수있는 모델이 Tree Induction for class Probability Estimation인데, 확률을 이용하여 sorting을 해서 속할확률에 대한 rank를 매길수있고, 이에따른 상위 x명에 대한 타겟마케팅이 가능해짐.

### Least Discriminant Analysis
타겟 변수가 3개 이상의 classification 문제일때 사용하는 방법론.

### Logistic Regression
- Linear Classifier을 사용할 경우, 이걸 기준으로 멀리 떨어지면 떨어질수록 class 에 belong 할 확률이 더 높아진다.
- 근데 문제는 확률은 0~1 사이고 classifier는 무한대임. 그래서 범위적인 차이가 너무큼.
  - Classifier로부터 거리를 확률로 변환. (0-1)
  - 사건이 일어날 가능성을 표현하는 승산(Odds) 구하기.
  - 이두가지를 이용하여 Log-odds 구함.
  - 그래서 Logistic Regression의 f(x)는 특정 class에 속할 log-Odds 구하는 것이 됨.
  - 이후 이 로그 승산을 속할 확률로 다시 변환 가능.

0.8 이상 correlation은 중복제거
대신 context에 대한 이해가 먼저 필요한 상태에서 결정하는게 중요.
drop the variable which is less correlated with the response
drop the variable which has larger Variance Inflation Factor (VIF)
fit 2 new models : one removing A and one removing B, and to see which new model suffers less multicollinearity. To measure multicollinearity, you can look at the VIF of each present variable or the Condition Number of 𝑋′𝑋 where 𝑋 is the present design matrix
use variable selection method like stepwise regression and lasso regression to (hopefully) remove one variable
