---
Title: "Killing zombie process"
Categories: Env
---

```
ps -ef | grep defunct | grep -v grep
```

좀비 프로세스 확인 가능

```
kill -9 <pid>
```

부모 강제 종료

```
ps -ef | grep <pid> | grep -v grep
```

pid의 부모 확인 가능

