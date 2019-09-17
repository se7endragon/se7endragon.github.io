---
layout: post
title: "Appled Deep Learning"
date: 2019-09-05
image: '/assets/img/'
description: 'Lecture 1'
categories:
- Lecture Notes
- DL
---
## Term Project
- term project은 github에서 배껴오기 금지.
- 작지만 데이터를 original data로 만들어야됨.
- 지금부터 토픽 정해서 고민해보는게 좋음.( Through Paper-Survey)

- Unsupervised Learning
  - 데이터의 패턴을 알고싶을때 (Clustering, 데이터 압축)
  - X가 들어갔을때 다시 X가 나오도록 하는것 (Reconstruction Error)
    - 이경우 중간 hidden layer 에 있는것들이 Feature

- Reinforcement Learning
  - 상태 -> 액션 에 대한 보상. (정답을 정확하게 가르쳐주는게아니라, 특정 액션이 몇점인지(Maximize the cumulative Reward))

- Semi-supervised Learning
  - Supervised + additional unlabeled Data
  - Unsupervised + additional labeled Data
  - Pretraining
  - labeled 데이터 적고 unlabeled data 많을 때
  - unlabeled data를 NN으로 학습시키고 labeled 데이터 이용하여 fine-tune.
  - One shot Learning (data balance is required)

- Transfer Learning
  - 이미 배운걸 전해주는거
  - Overfitting 문제 해소

- Deep Learning은 데이터가 많아도 performance decaying 현상이 ML에 비해 적음. (데이터가 적을땐 ML이 나음.)
  - 왜냐면 ML은 대부분 Feature Extraction에 시간을 보냄. (어떤 도메인에 대해 어떤 feature가 유의미하다는 GT가 있으면 그걸 extract.)
  - DL은 스스로 Feature을 학습함. (Train data를 통해 목적(Classification etc.)에 따라 적합한 relationship을 학습하기때문에 데이터가 커지면 새롭게 밝혀져야할 사실을 더 잘 학습하고 밝히는게 가능.

- 데이터의 패턴이 non-linear 하면 할 수록 레이어가 깊어야 표현이 가능.
  - 정확도는 높아지지만 너무 자세하게 표현하려고 하는 경향때문에 아웃라이어들까지 피팅이되버려서 오버피팅 문제도 생길수 있음.
  - 레이어가 많아지면 파라미터가 그만큼 증폭되기때문에 그만큼 많은 데이터가 있어야됨.
    - x와 y가 동시에 들어간 함수가있으면 x,y둘다 알아내기위해선 최소 두가지 function의 composite이 있어야됨.
    - 딥하면딥할수록 업데이트 펑션에서 1보다 작은 수들을 곱할때마다 gradient 가 작아지는 vanishing 현상때문에 로우레벨로 가면갈수록 더 잘 안되게됨.
