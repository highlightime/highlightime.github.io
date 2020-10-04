

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
```
