Detection 기술의 성능 평가 : 알고리즘의 파라미터 조절에 따라 유동적으로 변화

검출율 -> detection rate == recall : 대상 물체들을 빠뜨리지 않고 얼마나 잘 잡아내나?

프레임별로 구분하지 않고 총합을 이용해 계산함

ex) 첫 프레임 9/10검출, 두번째 0/1 일 경우 -> 9/11

정확도 -> precision == 검출된 결과 중 실제 물제가 얼마나 포함되었나?

# Precision(y) - Recall(x) Graph

파라미터(threshold,..) 조절에 따른 precision 과 recall 성능 변화 살펴보기

전반적 성능 파악에 유리 but 정량적 평가 불편

# AP (Average Precision)

Detection algorithm 의 성능 정량화

P-R 그래프 선 아래쪽 면적

# F-measure

P와 R의 조화평균

2 X (PXR) / (P+R)


# mAP (mean Average Precision)

각 클래스 별로 계산된 AP를 평균함

# Pascal VOC

IoU > 0.5 : true

IoU <= 0.5 : false

# Coco

IoU > 0.5,0.55,...,0.95 각각 기준으로 AP 계산 후 평균

Pascal VOC 방식이 정확도가 높은 정확도가 높은 detector들을 구분하지 못하는 단점 보완하기 위해 도입

# IoU

Area of Overlap / Area of Union

# Recall 

TP / ( TP + FN ) = TP / ground truths

# Precision

TP / ( TP + FP ) = TP / predictions



