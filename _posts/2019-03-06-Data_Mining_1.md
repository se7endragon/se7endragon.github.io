---
layout: post
title: "Data Mining Lecture #1"
date: 2019-03-06
image: '/assets/img/'
description: 'Lecture 1'
categories:
- Lecture Notes
- Data Mining
---
## Course Introduction: Data Science
최근에 화두가 되고있는 이유는 신기술 수용 속도의 증가한 것으로 볼 수 있음.
- Computing power
- Social Media
- IoT
- Cloud Computing

Structured data : numerical data stored in companies' db
Unstructured Data : video, audio, text

Data Engineer - data processing level.
Data Scientist - Data analysis + apply to decision making.

투자분야로서 data analytics 가 ROI 가 Information Technology분야에서 가장 높다고 함.
데이터 사이언스가 말단직원 뿐 아니라, 관리자 포지션에서도 알아야될 역량으로 부각되고 있다.

공대에서 접근하는 데이터 사이언스는 쏘왓이 없지만, 정보대학원에서는 디시젼메이킹에 연결시킨다고 함.

## 과목의 목표
- 데이터 관점에서 비즈니스 문제를 관찰하고 데이터에서 유용한 지식을 추출하는 원리 및 기법을 학습.

## What is Data Science
데이터 분석을 통해 현상을 이해하는 원리,절차,기법을 통칭
- 데이터 마이닝: 기술을 이용해 데이터에서 지식을 뽑아내는 기법
- 텍스트 마이닝
- 소셜네트워크 분석
- 데이터 시각화

궁극적 목표는
1. 더 나은 의사결정 (비즈니스 성과 증진)
2. Data-driven Decision Making: Wal-mart

** 항상 습관적으로 So What?에 대해 생각하기.

Always consider correlation/causation.

타겟 예제 : 어떤 물건을 사는 사람들은 어떠한 특성을 가진 사람들일것이다.

## 이 과목에서 관심을 가지는 데이터 주도 의사결정.
1. Decisions for which 'discoveries' need to be made within data (Target Case)
2. Decisions that repeat, especially at massive scale, and so decision making can benefit from even small increases in decision-making accuracy.
- 고객이탈 관리 의사결정에서, 이탈할것 같은 고객들에게 마케팅 비용을 쓰는 케이스.

## Analytics의 종류
- 기술적 분석(Descriptive Analytics): 과거 데이터로부터 이해를 얻는것. (통계학)
  - 무슨일이 언제 일어낫나?
  - 얼마나 영향을 주며 얼마나 자주 일어나는가?
  - 문제가 무엇인가?
- 예측 분석(Predictive Analytics): 통계적이고 기계학습적인 기법을 활용한 예측 모델링(데이터마이닝,예측모델링,ML,Prediction)
  - 다음에 뭔일이 일어날거같은가?
  - 만약 이런 트렌드가 지속된다면 어떻게 되는가?
  - 만약?
- 규범 분석(Prescriptive Analytics): 최적화 및 시뮬레이션 등에 의한 추천 의사결정(Simulation,제약기반최적화, 다목적 최적화, 글로벌 최적화) <- 조금 산업공학쪽 주제
  - 최적의 대답은 뭔가?

## Data Mining
- 데이터 속의 유용한 패턴을 찾아내는 것.

#### 주요기법
- 예측 (주어진 data에 근거하여 모델을 만들고 모델을 이용하여 새로운 케이스들에 대한 예측)
- 분류 (사전에 분류된 케이스들이 있을때, 어디에 속하는 지를 결정.)
- 군집 (데이터의 여러 속성들을 비교하여 유사한 특성을 갖는 항목들을 함께 군집시키는 것)
- 연관규칙 (한 패턴의 출현이 다른 패턴출현을 암시하는 속성이나 항목간의 관계를 파악)

#### 기법별 used algorithms
- 군집화 : K-means, 밀도기반 군집화. (데이터셋 내의 속성들을 기준으로 하여 데이터셋의 데이터 포인트들을 군집으로 구별함.)
- 분류 : Decision Tree, NN, Bayesian, k-NN, Logistic Regression, SVM, Linear classification. (데이터 포인트가 미리 정의된 클래스 중 어디에 속하는지에 대해 예측.)
- 연관성 분석 : FP-Growth, Apriori (거래데이터를 기반으로 항목 집합내의 관계 식별, Recommendation System)
- 회귀 분석 : Regression (수치형 타겟변수 예측)
- 이상 탐지 : 거리기반, 밀도기반, 지역특이값 요소(Local Outlier Factor) (특정 데이터 포인트가 데이터셋의 다른 데이터 포인트와 비교하여 특이값인지 예측)
- 시계열 분석 : Regression, Autoregressive Integrated Moving Average (과거의 값에 기반하여 미래의 타겟 변수 값 예측)

##### 데이터 과학자는 알고리즘 사용자이지 개발자가 아니다
- 있는 알고리즘을 어떻게 잘 활용할 것인가!

기계학습 기반 모델 개발 프로세스
1. 모델에 사용될 variable 선정
2. 수집
3. 학습.
4. 모델완성햇으면 검증 후 적용여부결정.

영화흥행요인 예측 모델 설계 예제
1. 기사 자료에서 영화 흥행에 영향을 미치는 변수 도출.
2. 추가조사를 통해 외부변수 도출.
