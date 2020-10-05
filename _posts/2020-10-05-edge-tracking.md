---
title: "Edge Tracking"
categories: Vision
---

Double Thresholding 을 통해 구분된 weak edges가 edge인지 아닌지 확인
- weak edge에서 인접한 8방향으로 확인해 strong edge와 연관성 확인

```python
d = np.array([[1, 1, 1, 0, 0, -1, -1, -1], [1, 0, -1, 1, -1, 1, 0, -1]])
def trackEdge(img, i, j, weak=127, strong=255): 
    img[i, j] = strong
    idxs = np.array([[i], [j]]) + d
    for p,q in zip(idxs[0], idxs[1]):
        try:
            if img[p,q] == weak: trackEdge(img, p, q)
        except IndexError:
            pass
```

```python
def hysteresis(img, weak, strong=255): 
    strongIdx = np.where(img == strong)
    for i, j in zip(strongIdx[0], strongIdx[1]): 
        idxs = np.array([[i], [j]]) + d
        for p,q in zip(idxs[0],idxs[1]):
            try:
                if img[p,q]==weak:
                    trackEdge(img, p, q)
            except IndexError:
                pass

    weakIdx=np.where(img==weak)
    for i, j in zip(weakIdx[0],weakIdx[1]):
        img[i,j]=0

    return img
```
