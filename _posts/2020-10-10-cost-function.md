---
title: Cost function
category: Vision
tag: NN
---
가설함수 h_𝜃(x)=𝜃_0+𝜃_1x
오차 값 (Error) h_𝜃(x)-y

- 목적: 오차가 가장 적은 𝜃를 구하여 가설함수 h를 정하는데 도움

# Mean Square Error
```
J(𝜃_0, 𝜃_1)= 1/2m ∑𝑖=1𝑚(ℎ𝜃(𝑥(𝑖)−𝑦(𝑖))2
```

2로 나누어줌 <- 미분시 계산 편리함을 위해


# Average Cross Entropy
- 목적: sigmoid 와 MSE 결합시 학습 속도 저하 해결

Cross entropy : 2개의 확률분포 차이 나타냄

2개의 확률 분포 p, m 에 대한 Cross entropy
```
H(p,m) = -sigma_i p(xi)log(m(xi))
```



