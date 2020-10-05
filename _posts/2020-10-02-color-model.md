---
title: "Color Model"
categories: vision
---
# Gray Model

(255)

# RGB Model

(r1, g1, b1) , (r2, g2, b2)

유클리디언 거리를 이용해 두 색의 차이 계산

'd = sqrt{(r1-r2)^2 + (g1-g2)^2 + (b1-b2)^2}'

* 밝기 정보 제거 -> normalized rg : (r = R/(R+G+B), g = G/(R+G+B))

but 밝기값 매우 어두운 경우에는 불안정

# HSV Model

(h1, s1, v1) , (h2, s2, v2)

직관적 해석 가능

색조 Hue : 붉은색 - 푸른색

채도 Saturation : 무채색 - 선명한색

명도 Value : 어두움 - 밝음

Hue 채널만을 사용할 경우에는 

'd = |h1 - h2|'

모든 채널을 사용, Euclidean 거리를 이용

'd = sqrt{(h1-h2)^2 + (s1-s2)^2 + (v1-v2)^2}'

# YCbCr Model (YUV)

RGB 색에서 밝기(Y)와 색차정보(Cb, Cr)를 분리해 표현하는 색상 모델

인간의 눈이 밝기차에 민감 but 색차에는 둔감

Y에 많은 비트수 (해상도) 할당

Cb, Cr에는 낮은 비트수 할당하는 방식으로 비디오 압축

별도의 색상변환 필요하지 않음

