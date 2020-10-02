# mAP (mean Average Precision)

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



