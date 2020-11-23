---
title: [yarn] Error Command failed with exit code 127.
Category: Web
---

## Reference

https://github.com/facebook/create-react-app/issues/1155

https://classic.yarnpkg.com/en/docs/cli/run

## What?

디렉토리에서 yarn start 가 동작하지 않음

 => react script not found error message

## Why?

git 저장소에서 받은 프로젝트와 설치된 yarn 버전 상이함

=> Upgrade 문제

## How?

Updates Yarn to the latest version.

```
yarn self-update
```

이제 동작하지 않음

이유 : https://classic.yarnpkg.com/en/docs/cli/policies/#toc-policies-set-version

```
npm -g install yarn
yarn
```

동작함

## The end

React script in pacjage.json file



