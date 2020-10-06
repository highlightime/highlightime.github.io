---
title: Activation Function
categoty: Vision
tag: CNN
---

# Activation Function
Filter 를 통해 얻은 Feature map에 Activation Function 적용

- 선형적 값을 비선형적인 값으로 바꿈
- 뉴런이 다음 뉴런으로 보내는 기준치 이상 신호를 결정 

# Sigmoid 
참에 가까우면 0.5~1, 거짓에 가까우면 0~0.5

x=0 일때 기울기 최대 미분값 1/4
- Gradient Vanishing: Back Propagation 이 layer가 깊어질수록 작동하지 않는 문제점 ( 작은 미분값 .. 사라짐 )
- Gradient Exploding : 미분값 > 1 일 때 여러번 곱하면 발산

# tanh
- Sub Sampling(Pooling) 방법으로 Max Pooling

x=0 일때 기울기 최대 미분값 1 -> 그래도 Gradient Vanishing 

# ReLu
R(z) = max(0,z)
- Gradient Vanishing 해결
- Sub Sampling(Pooling) 방법으로 Average Pooling
- exp()함수가 없기에 학습 6배 빠름



# CNN 
1. Convolution Filter

2. Activation Function

3. Pooling (Subsampling)
