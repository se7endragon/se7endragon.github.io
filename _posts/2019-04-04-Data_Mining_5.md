---
layout: post
title: "Data Mining Lecture"
date: 2019-04-04
image: '/assets/img/'
description: 'Lecture 5'
categories:
- Lecture Notes
- Data Mining
---

# Overfitting and its Avoidance

### Overfitting
모집단에 없는 특성을 모델링 하는 것
- 아직 학습하지 않은 데이터에 대한 일반화를 희생하고, 훈련 데이터에만 모델을 맞추는 경향
- 모델은 훈련 데이터를 가져온 모집단에도 정확히 적용될 수 있어야 함

#### 일반화
- 모델이나 모델링 프로세스의 특성을 말함
- 모델 제작에 사용되지 않은 모든 데이터에도 모델을 적용할 수 있는 성질

### 과적합화가 왜 문제인가?
과적합화 문제는 모델의 성능을 악화시키기 때문이다.
- 모델이 복잡해지면서 해로운 가짜 연관성까지 학습하게 되기 때문
- 가짜연관성은 훈련 세트에만 존재하는 특이한 성질

### 과적합화 검사
적합도 그래프(Fitting Graph)
- 모델의 복잡도에 따른 모델의 정확도를 보여줌.
  - 모델의 복잡도는 변수의 수가 많을 수록 높아짐 (Curse of Dimensionality)
- 모델을 훈련 데이터 세트에 적용한 성능 vs 예비 데이터에 적용해 추정한 모델의 일반화 정확도.

예비 데이터(Test Data)란 타겟 변수값을 예측할 실제 데이터는 아니지만, 실험실에서 모델의 일반화 성능을 측정하기 위해 떼어놓는 데이터.

적합도 그래프란 모델의 복잡도에 따라 훈련 데이터와 예비 데이터에 대한 모델의 정확도 추정치 변화를 나타내는 그래프.

##### 모델 복잡도 요인
- 테이블 모델의 경우테이블에 들어 있는 데이터 row 수를 복잡도 척도로 함(데이터의 observation 수가 일정 개수 이상 들어가면 계산량만 증가하고 학습효과는 비슷하기때문에)
- Decision Tree의 경우, 노드 수가 복잡도 척도
- 선형판별분석에서 변수 갯수가 복잡도 척도
- 모델이 충분히 복잡하지 않으면 정확도는 오히려 떨어짐. (즉 complexity가 높을 수록 학습모델 정확도가 올라감.)
- 그래서 적절한 complexity를 내포하는 모델이 좋은 모델.
- Decision Tree에선 Pruning을 통해 Overfitting 피함.

Logistic Regression이 상대적으로 과적합화에 더 민감함. 왜냐하면 Least Square Apprioximation 방식을 사용하므로 개별 데이터의 영향을 더 받음.(High Variance)
SVM은 덜 민감함. 경계선 상에서 가장 폭이 넓은 선을 선택하는 원리이기때문.

과적합화 문제는 훈련 데이터의 비정상적 편향 때문에 발생한것은 아니다. 표본 추출 방법이 편향되어 있지 않더라도 표본에 변이가 있을 수 있기 때문.
또한 모델의 과적합화되어 있는지 미리 알 수 있는 일반적인 분석 방법은 없다. 예비 데이터를 이용해서 과적합화 여부를 알아내는것이 좋음.

### Test Data 평가에서 교차검증까지
- 오버피팅 문제 해결하기전에, train accuracy와 test accuracy를 비교해서 존재 여부를 알아내야함.
- Cross Validation
  - 정교한 예비 훈련 및 시험 절차
  - 여러번 분할하고 시험하기 위한 표본을 체계적으로 바꿔가면서 모든 데이터에 대해 추정치 계산
  - 일반화 성능을 한번만 추정하는 대신, 데이터 세트에 따라 성능이 어떻게 바뀔 지 예측함.
  - test data결과에 대한 변이를 파악.
  - Random Sampling 한번 대신에 fold 수 만큼 분할샘플링 후, 각 분할세트를 모두 train-test로써 돌려본 후 정확도평균내서 검증.
  - fold 내의 각 fold당 accuracy들의 std가 고르면 고를수록 fold 전체합산 평균정확도와 비슷하게 나온다는 뜻이므로, 일관성있는 모델, 즉 오버피팅이 덜 한 모델이라고 결론 지을 수 있다.

- Generalization
  - 어떤 알고리즘을 쓰는지에 따라 달라질수있다.
  - train/test 어케 뽑아내는지에따라서도 달라질수있다.
  - instance size가 얼마나있는지에 따라서도 달라질수있다.
    - DT(좋은 융통성)에 비교해서 Logistic Regression(융통성 없음)이 적은 sample size로도 모델링 완성 가능.

#### Complexity 제어법
1. 하나의 모델에서 과적합화를 피하려면 데이터에서 유도된 모델의 복잡도 제어 필요.
  - 트리
    - Pre-Pruning: 너무 복잡해지기 전에 트리의 성장을 멈추게 함.(각 노드의 object 개수의 최소치를 정하고/최대 트리 깊이도 정함)
    - Post-Pruning: 트리를 최대한 키운 후에 Pruning해서 크기 줄임.(정확도가 떨어지지 않는다면 프루닝 ㄱㄱ)
  - 선형 함수 모델
    - Feature Selection(Forward,Backward)
2. 복수의 모델 중 오버피팅 정도를 비교하고 싶으면 Cross-Validation 통해 체크 가능. (Nested Cross-Validation)
  - Sequential Forward Selection
    - single var model(p만큼) 만들고 최고를 뽑음
    - 그담에 최고single var vs 최고double var비교해서 다시최고뽑음.
    - var 추가해도 검증데이터에 대한 정확도가 높아지지 않으면 처리 중단.

  - Sequential Backward Elimination
    - literally backwardly eliminate the variables.

#### Conclusion
Feature Selection 을 진행하면서 Cross Validation까지 넣는게 가장 좋은 방법인듯.
