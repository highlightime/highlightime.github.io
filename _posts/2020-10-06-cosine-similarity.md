---
title: Consine Similarity
category: Math
---

# Consine Similarity 
두 벡터간의 코사인 각도를 이용해 구하는 두 벡터의 유사도

A*(내적)B/|A||B|

# Using in Word Vector
문서1 : 저는 사과 좋아요
문서2 : 저는 바나나 좋아요
문서3 : 저는 바나나 좋아요 저는 바나나 좋아요

위의 세 문서에 대해서 문서 단어 행렬을 만들면 이와 같습니다.

바나나	사과	저는	좋아요

문서1	  0	1	1	1

문서2	  1	0	1	1

문서3	  2	0	2	2

```python
doc1=np.array([0,1,1,1])
doc2=np.array([1,0,1,1])
doc3=np.array([2,0,2,2])
print(cos_sim(doc1, doc2)) #문서1과 문서2의 코사인 유사도
print(cos_sim(doc1, doc3)) #문서1과 문서3의 코사인 유사도
print(cos_sim(doc2, doc3)) #문서2과 문서3의 코사인 유사도 = 1, 모든 단어 수의 빈도가 같을시 동일 문장이라 판단 
```

# Using in Recommend System
```python
from sklearn.feature_extraction.text import TfidfVectorizer
# overview에 대해서 tf-idf 수행
tfidf = TfidfVectorizer(stop_words='english')
tfidf_matrix = tfidf.fit_transform(data['overview'])


from sklearn.metrics.pairwise import linear_kernel
cosine_sim = linear_kernel(tfidf_matrix, tfidf_matrix)
```

# Code
```python
from numpy import dot
from numpy.linalg import norm
import numpy as np
def cos_sim(A, B):
       return dot(A, B)/(norm(A)*norm(B))
```
