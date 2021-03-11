---
title: "View Binding"
date: 2021-03-11T16:23:00+09:00
description: ""
categories: [
    "android"
]
tags: [
    "android"
]
type: "post"
draft: true
---
View binding 에 대해 알아볼것   

<!--more-->

### View Binding
이전까진, 대부분의 경우 View 를 결합하기 위해 findViewById() 를 사용했음.   
View Binding 을 사용하면 좀더 쉽게 View 를 컨트롤 할 수 있다.   

### Gradle 설정
View binding 사용하기 위해선, 먼저 viewBinding 요소를 gradle 에 추가해야됨.
```gradle
android{
    ...
    viewBinding{
        enabled = true
    }
}
```

### Usage
위처럼 View Binding 이 설정되면, XML layout 파일의 Binding class가 생성됨.   
형식은 XML 이름 + Binding.   
예를들어, result_profile.xml 파일이 있는경우 Binding class 의 이름은 **ResultProfileBinding**   
```xml
<LinearLayout ... >
    <TextView android:id="@+id/name" />
    <ImageView android:cropToPadding="true" />
    <Button android:id="@+id/button"
        android:background="@drawable/rounded_button" />
</LinearLayout>
```
이런 Layout 이 있을 경우, TextView, Button 은 ID 가 있기 때문에 Binding class 통해 참조 가능하지만 ImageView 의 경우에는 ID 가 없어 참조 불가하다.   

#### Usage in Activity
inflate() 호출해 getRoot() 메소드로 root view 참조
```kotlin
override fun onCreate(savedInstanceState: Bundle) {
    super.onCreate(savedInstanceState)
    binding = ResultProfileBinding.inflate(layoutInflater) // XML 파일로 class 결정
    val view = binding.root
    setContentView(view)
}
```
각 child view 는 아래처럼 참조 가능
```kotlin
binding.name.text = viewModel.name
binding.button.setOnClickListener { viewModel.userClicked() }
```   

### Usage in Fragment






