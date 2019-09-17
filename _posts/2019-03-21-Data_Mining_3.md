---
layout: post
title: "Data Mining Lecture"
date: 2019-03-21
image: '/assets/img/'
description: 'Lecture 3'
categories:
- Lecture Notes
- Data Mining
---

# 예측모델링: 연관성에서 감독 세분화까지

- Training Data로 모델을 만드는 과정은 귀납법에 해당함.
  - 귀납법이란 이미 일어난 instance를 바탕으로 모델을 만드는것.
  - 연역법이란 이미 있는 모델을 새로운 instance에 적용하는것.

#### Decision Tree
- Supervised Segmentation
  1. 어떤 변수가 타겟 변수에 대한 중요한 정보를 담고 있나?
    - 정보를 전달하는 속성의 선택(Entropy)
  2. 얼마나 많은 정보를 담고 있나?
    - 엔트로피의 변화 측정(Information Gain)
  3. 타겟값을 예측할 수 있는 순서대로 변수들의 순위를 매길 수 있나?
    - 정보량을 가장 많이 증가시키는 속성 선택(IG순위 체크해서 랭크)

- 정보를 전달하는 속성의 선택
  - 타겟 변수 예측 시, 더 많은 정보를 제공하는 변수를 추출하기 위한 attribute을 골라야 함
    - 데이터 속성이 많을 때 복잡성을 줄여줌
    - 데이터 세트의 크기를 상당히 줄여줌
    - 모델의 정확도 향상
  - 세그먼트가 가능한 순수한(pure) 그룹이 되도록 해야함.
    - 순수 = homogeneity
    - 그룹 안에 들어 있는 사람들이 모두 동일한 타겟 값을 갖고 있으면 이 그룹은 homogeneous
    - 순도의 측정은 Purity measure, a.k.a. Entropy
  - 현업에서 데이터 분류할 때 순수하게 세분화하는 변수를 찾아내는 경우는 드물다. 그래서 try your best

- Entropy
  - 범주형 변수에 대한 분할을 평가하는 순수도 척도
  - 낮을수록 순수
- Information Gain
  - 부모 class 보다 자식 class들의 entropy가 얼마나 변하는지.

- 트리 구조를 활용한 감독 세분화
  - 정보량을 증가시키는 속성을 여러개 선택해야할때 어케 결합할까?
    - Multivariate Supervised Segmentation

- 계층 확률 추정
  - Binary classification 말고 Probability를 Decision Tree에 적용.
  - 객체 수가 너무 적을때는 최종확률이 너무 낙관적으로 나오므로(Overfitting) 라플라스 교정법을 적용.

- Decision Tree Criterions
  - C4.5 (Gain Ratio) as splitting Criterion
    - C5.0 improves misclassification costs
  - Cart uses Gini Index as primary splitting criterion

- Decision Tree Pros
  - Outlier에 영향 받지 않음.
  - Linearity/Normality/Equality of distribution not assumed.
  - Finds more than 2 IVs that has High interpretability
  - Both continuous and nominal used.

- Decision Tree cons
  - Overfitting Possibility
  - Error comes out from treating continuous var as non-continuous
  - Relatively low accuracy

##### Summary Statistics를 보면서 무슨작업을 할지 결정해야함.
- Target Var의 비율이 너무 편향적일 경우, Data Balancing 작업 필요.
- Oversampling vs downsize sampling
- Decision Tree Learner's PMML Setting
  - returnLastPrediction?
- in KNIME, partitioning node's upper arrow is training, lower arrow is test.
- inner join (and) outer join (or)
- column filter 걸기 전 correlation 분석 하는게 좋음.
