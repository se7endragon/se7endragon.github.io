---
layout: post
title: "Data Mining Lecture"
date: 2019-05-09
image: '/assets/img/'
description: 'Lecture 9'
categories:
- Lecture Notes
- Data Mining
---
# 증거와 확률

- 증거 : 타깃 값에 도달하게 만드는 객체의 특징
- 증거력 : 각 특징이 타깃 값에 도달하게 만드는 정도

조건부 확률(Conditional Probability) : E라는 가정하에 C의 확률.

Bayesian : P(A|B) = (P(B|A) * P(A))/P(B)
즉, Probability of A given B == Probability of B given A times Probability of A divided by Probability of B

Naive Bayes : Assumption of evidences are independent

### 나이브 베이즈의 특성
- 상당히 단순하고 특징 간의 엄격한 독립성을 가정(조건부 독립)
- 독립성 가정이 잘못된 경우에도 분류성능이 그리 떨어지지 않기 때문에 나이브 베이즈 분류자는 데이터를 분류하는 실무 작업에서 놀라울 정도로 뛰어난 성능을 보여줌.

독립적인 특성이 많을때 분자에 알아내고자 하는 확률의 given으로써 n개만큼 쓸수있음. 예를 들어, 미사어구를 쓸때 특정 성과에 관한 확률을 구하고싶을때, 미사어구를 3개 정도 샘플을 두고 보고싶을때, 분자에 성과가 안좋은 놈들이 미사어구A를 쓸 확률 X 성과가 안좋은 놈들이 미사어구 B를 쓸 확률... 등으로 해서.

Naive Bayes의 목적은 정확한 확률이 아니라 분류가 목적임.

- Class 분류 문제인 경우, 모든 c 계층 중에서 어느 계층에 대한 p(c|E)가 가장 큰지만 알면 됨.
- 예를 들어, 호텔 예약(c0) vs 안예약(c1) 해서 두개다 E가 given일때의 p를 구하고, 둘중 뭐가 더 큰지를 확인하면 됨.

여기서 문제가 있을 수 있는데, E중 하나가 0일 경우 분자끼리 곱하기 이므로 모두 0이되어버리는 사태가 일어날수있음. 그래서 Laplas Smoothing을 이용하여 low-frequency problem을 해결 가능.

### 증거 향상도
Lift는 Classifier를 평가하는 척도중 하나인데, 이걸 나이브 베이즈 계산식의 분자로써 대신 들어간다면 각 evidence(feature)들이 타깃 클래스의 확률로써 곱해짐. P(C|E) = P(C) * lift(E)
