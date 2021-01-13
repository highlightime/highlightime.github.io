---
title: vm ubuntu shared files
categories: VM
tags: VM, Ubuntu, Sharing
published: true

---



☑️ 로컬 저장공간에서 공유하고싶은 파일 shared 설정하기

☑️ vm ubuntu에서 shared folders 설정하기

![Screen Shot 2021-01-13 at 5.47.10 PM](/Users/yunhyeong/Library/Application Support/typora-user-images/Screen Shot 2021-01-13 at 5.47.10 PM.png)



☑️ 터미널에서 접근

```
sudo mkdir ~/mnt/share
sudo mount -t vboxsf [공유파일이름] /mnt/share
```

