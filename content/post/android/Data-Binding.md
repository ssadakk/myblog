---
title: "Data Binding"
date: 2021-03-12T15:47:02+09:00
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
Data Binding 에 대한 정리

<!--more-->

[참고사이트](https://developer.android.com/topic/libraries/data-binding/expressions)   


## Data Binding 이 뭔데
간단히 말해, 기존 아래와 같은 코드를
```kotlin
findViewById<TextView>(R.id.sample_text).apply {
    text = viewModel.userName
}
```
아래처럼 쓸 수 있는것
```html
<TextView
        android:text="@{viewmodel.userName}" />
```

## What to do to use?
Gradle 에 아래와 같이 추가 (View binding 과 같다)
```gradle
android {
        ...
        dataBinding {
            enabled = true
        }
    }
```

## Data Binding
View binding 과 마찬가지로, layout name + Binding 으로 데이터 바인딩 클래스 생성됨.   
e.g) activity_main.xml -> ActivityMainBinding   

## Layout binding & expression
```xml
<?xml version="1.0" encoding="utf-8"?>
    <layout xmlns:android="http://schemas.android.com/apk/res/android">
       <data>
           <variable name="user" type="com.example.User"/>
       </data>
       <LinearLayout
           android:orientation="vertical"
           android:layout_width="match_parent"
           android:layout_height="match_parent">
           <TextView android:layout_width="wrap_content"
               android:layout_height="wrap_content"
               android:text="@{user.firstName}"/>
           <TextView android:layout_width="wrap_content"
               android:layout_height="wrap_content"
               android:text="@{user.lastName}"/>
       </LinearLayout>
    </layout>
```
User 라는 클래스가 있다고 가정, TextView 에서 User 의 firstName, lastName 을 갖다쓰는걸 볼 수 있다.   
@{} 구문을 사용.

그렇다면 데이터 결합은? 아래처럼   
```kotlin
override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)

    val binding: ActivityMainBinding = DataBindingUtil.setContentView(
            this, R.layout.activity_main) // View binding 에서처럼 inflate() 를 이용할 수도 있다.

    binding.user = User("Test", "User")
}
```
binding.user 로 Test user 가 들어가겠지   

Fragment, listView, RecytclerView 같은 어댑터 내에서 Binding 하는 경우는 DataBindingUtil.Inflate() 사용할 수 있음
```kotlin
val listItemBinding = ListItemBinding.inflate(layoutInflater, viewGroup, false)
    // or
val listItemBinding = DataBindingUtil.inflate(layoutInflater, R.layout.list_item, viewGroup, false)
```







