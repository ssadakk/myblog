---
title: "Live Data"
date: 2021-03-16T23:22:56+09:00
description: ""
categories: [

]
tags: [
    
]
type: "post"
draft: true
---

<!--more-->

## Live Data?
LiveData 는 데이터 홀더 클래스. 특이한 점은 LiveData 는 수명 주기를 인식한다. Activity, fragment, service 의 라이프사이클을 모두 인식. 이를 통해 활둥 상태에 있는 Observer 만 update 한다.

## Live Data의  이점
- UI 와 Data 상태 일치 보장
- Memory leak 없음
- Stop 상태로 인한 비정상 종료 없음
- LifeCycle 을 수동으로 처리하지 않는다.
- 최신 데이터 유지
- 적절한 구성 변경
- 리소스 공유

##

