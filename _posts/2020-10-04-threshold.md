# Threshold

```python
def threshold(img, lowThresholdRatio=0.05, highThredholdRatio=0.09): 
  highThreshold = img.max() * highThredholdRatio
  lowThreshold = highThreshold * lowThresholdRatio
  
  M, N = img.shape
  res = np.zeros((M, N), dtype=np.int32)
  
  weak = np.int32(127) 
  strong = np.int32(255)
  
  strong_i, strong_j = np.where(img >= highThreshold) 
  zeros_i, zeros_j = np.where(img < lowThreshold)
  weak_i, weak_j = np.where((img < highThreshold) & (img >= lowThreshold))
  
  res[strong_i, strong_j] = strong res[weak_i, weak_j] = weak
return (res, weak, strong)
```

# Global thresholding

하나의 이미지에 전역으로 하나의 문턱값을 이용함

```cv2.threshold(img,threshold_value,value,flag)```

*img*: Grayscale 이미지
*threshold_value*: 픽셀 문턱값
*value*: 픽셀 문턱값보다 클 때 적용되는 최대값(적용되는 플래그에 따라 픽셀 문턱값보다 작을 때 적용되는 최대값)
*flag*: 문턱값 적용 방법 또는 스타일
**cv2.THRESH_BINARY**: 픽셀 값이 threshold_value 보다 크면 value, 작으면 0으로 할당
**cv2.THRESH_BINARY_INV**: 픽셀 값이 threshold_value 보다 크면 0, 작으면 value로 할당
**cv2.THRESH_TRUNC**: 픽셀 값이 threshold_value 보다 크면 threshold_value, 작으면 픽셀 값 그대로 할당
**cv2.THRESH_TOERO**: 픽셀 값이 threshold_value 보다 크면 픽셀 값 그대로, 작으면 0으로 할당
**cv2.THRESH_TOZERO_INV**: 픽셀 값이 threshold_value 보다 크면 0, 작으면 픽셀 값 그대로 할당


# Adaptive thresholding

광원 조건에 따라 이미지 프로세싱

이미지의 서로 다른 작은 영역에 적용되는 문턱값 계산해 적용

```cv2.adaptiveThreshold(img,value,adaptiveMethod,thresholdType,blocksize,C)```

*img*: Grayscale 이미지
*value*: adaptiveMethod에 의해 계산된 문턱값과 thresholdType에 의해 픽셀에 적용될 최대값
*adaptiveMethod*: 사용할 Adaptive Thresholding 알고리즘
**cv2.ADAPTIVE_THRESH_MEAN_C**: 적용할 픽셀 (x,y)를 중심으로 하는 blocksize x blocksize 안에 있는 픽셀값의 평균에서 C를 뺀 값을 문턱값으로 함
**cv2.ADAPTIVE_THRESH_GAUSSIAN_C**: 적용할 픽셀 (x,y)를 중심으로 하는 blocksize x blocksize안에 있는 Gaussian 윈도우 기반 가중치들의 합에서 C를 뺀 값을 문턱값으로 함
*blocksize*: 픽셀에 적용할 문턱값을 계산하기 위한 블럭 크기. 적용될 픽셀이 블럭의 중심이 됨. 따라서 blocksize는 홀수여야 함
*C*: 보정 상수로, 이 값이 양수이면 계산된 adaptive 문턱값에
