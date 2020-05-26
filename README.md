# 안드로이드 개발 기능 모음
1️⃣Textview에서 지정해준 크기보다 넘어가면 ... 으로 처리해주는 방법<br/>
2️⃣gif 이미지 처리 방법<br/>
3️⃣radio button 여러 줄로 처리하는 방법<br/>
4️⃣constraintlayout의 여러가지 기능<br/>
5️⃣Bottom sheet Behavior 사용

🌀계속해서 추가 예정이에요〰️
<br/>
<br/>
<br/>
<br/>
⬇️⬇️⬇️⬇️⬇️⬇️⬇️⬇️⬇️⬇️⬇️⬇️⬇️⬇️
<br/>
<br/>
<br/>
<br/>
## 📌 Textview에서 지정해준 크기보다 넘어가면 ... 으로 처리해주는 방법

 * maxLines: 텍스트 라인 수를 지정해주는 설정 ➡️ 1,2,3, ...
 * ellipsize: 일정 글자수가 넘어가면 어떻게 처리를 할지 설정 ➡️ start, middle, end, none, ...

 ```
 <TextView
      android:layout_width="50dp"
      android:layout_height="wrap_content"
      android:text="yanghyesun"
      maxLine="1"
      ellipsize="end"/>
 ```

<br/><br/>

## 📌 gif 이미지 처리 방법

* Glide 라이브러리를 사용!

  서버와 통신하기 전에 loading으로도 많이 쓰입니다 :) 서버와 통신하기 전 보여주고 successful 하면 안보여지게 처리해주면 되겠죠 ❓

  1️⃣ res 폴더 안에 raw 폴더를 만들어준 다음, gif 파일을 넣어주세요.

  2️⃣ kotlin 처리
```
Glide.with(this).load(R.raw.loading).into(img_id)
```

<br/><br/>

## 📌 radio button 여러 줄로 처리하는 방법

예를 들어서,

<img width="228" alt="스크린샷 2020-05-27 오전 2 00 57" src="https://user-images.githubusercontent.com/37995236/82929004-f79b3200-9fbd-11ea-8883-d4821b1a714b.png">
이런 형식으로 되어 있다면 RadioGroup 태그를 2개 만들어야 하고 2개의 그룹을 같이 처리해줘야 합니다.

이를 쉽게 해결해주는 라이브러리가 있어요 ‼️

✅ __multiradio 라이브러리 이용__ ✅

  1️⃣build.gradle 에 추가
```
implementation 'com.yuxingxin.multiradiogroup:library:1.0.0'
```

  2️⃣xml 파일
 ```
  <com.yuxingxin.library.MultiRadioGroup
    android:id="@+id/multi_rg"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    <RadioGroup
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal" >
        <RadioButton
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="A"
            />
        <RadioButton
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="B"
            />
        ...
        ...

    </RadioGroup>
    <RadioGroup
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal">
        <RadioButton
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="D"
            />
        <RadioButton
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="E"
            />
        ...
        ...

    </RadioGroup>
</com.yuxingxin.library.MultiRadioGroup>
 ```
 <br/><br/>
 
## 📌 constraintlayout의 여러가지 기능
 * layout_constraintWidth_percent : 부모 뷰에서 percent 수만큼 width 차지  ➡️ 0.3 (30% 차지), ...
   layout_constraintHeight_percent : 부모 뷰에서 percent 수만큼 height 차지  ➡️ 0.6 (60% 차지), ...
> 
> 사용할 시 width, height 를 0dp로 설정!
> 
> 안드로이드 기기가 커지든 작든 부모 뷰의 percent 만큼 차지
> ```
> <ImageView
>       android:layout_width="0dp"
>       android:layout_height="0dp"
>       app:layout_constraintWidth_percent="0.8"
>       app:layout_constraintHeight_percent="0.4" />
> ```

 * layout_constraintDimensionRatio : 가로,세로 비율 설정
> 
> ```
> <ImageView
>       android:layout_width="0dp"
>       android:layout_height="0dp"
>       app:layout_constraintDimensionRatio="1:1" />
> ```

* group 태그
> 
> 2개의 뷰를 묶어 visibility를 한번에 처리 가능!
> ```
> <TextView
>         android:id="@+id/tv1"
>         android:layout_width="wrap_content"
>         android:layout_height="wrap_content"
>         android:text="tv1" />
> 
>     <TextView
>         android:id="@+id/tv2"
>         android:layout_width="wrap_content"
>         android:layout_height="wrap_content"
>         android:text="tv2" />
> 
> 
>     <androidx.constraintlayout.widget.Group
>         android:id="@+id/group1"
>         android:layout_width="0dp"
>         android:layout_height="0dp"
>         android:visibility="gone"
>         app:constraint_referenced_ids="tv1,tv2" />
> ```
* chain 속성
<img width="632" alt="스크린샷 2020-05-08 오후 11 27 37" src="https://user-images.githubusercontent.com/37995236/81416356-903f4e80-9184-11ea-8780-3f688c18d56d.png">

<br/>
<br/>

## 📌 Bottom Sheet Behavior 사용

카카오맵에서 장소를 클릭하면 나오는 작은 화면을 기억하시나요❓

➡️ 이런 형태로 하단에 뷰가 있을시 처리 해주고 싶을 때 사용!

<img width="304" alt="스크린샷 2020-05-27 오전 3 26 39" src="https://user-images.githubusercontent.com/37995236/82936831-21f2ec80-9fca-11ea-95ce-f45c76b4553e.png">

<br/>

1️⃣Bottom Sheet 뷰 만들기<br/>
* layout_behavior="com.google.android.material.bottomsheet.BottomSheetBehavior" 필수로 설정 ❗️
* behavior_peekHeight : bottom sheet 뷰의 기본 높이를 설정
* behavior_hideable : 사용시 스크롤시 true면 숨겨지고, false면 숨겨지지 않도록 설정
```
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:behavior_peekHeight="620dp"
    app:behavior_hideable="true"
    app:layout_behavior="com.google.android.material.bottomsheet.BottomSheetBehavior"
    android:clickable="true">
    
    <!-- bottom sheet 뷰 영역 -->
    
</androidx.constraintlayout.widget.ConstraintLayout>
```

2️⃣CoordinatorLayout 태그 이용<br/>
```
<androidx.coordinatorlayout.widget.CoordinatorLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent">
        
        
        <!-- 원래 뷰 화면 영역 -->
        
        
        <!-- bottom sheet가 보여지면 뒷배경 처리 -->
        <View
            android:id="@+id/bottom_sheet_blur"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:background="#aa000000"
            android:visibility="gone"/>
            
        <!-- bottom sheet 뷰 : xml 파일로 만들어서 include 해주기 -->
        <include
            android:id="@+id/bottom_sheet_view"
            layout="@layout/bottom_sheet_view" />
</androidx.coordinatorlayout.widget.CoordinatorLayout>

```

3️⃣kotlin 처리
* BottomSheetBehavior.from() 메서드로 bottome sheet 설정
* state

  ✔️ STATE_COLLAPSED : height 만큼 처리<br/>
  ✔️ STATE_HIDDEN : 숨김 처리<br/>
  ✔️ STATE_EXPANDED : 가득 차게 처리

```
 val bottomSheet: BottomSheetBehavior<View> = BottomSheetBehavior.from(bottom_sheet_view)
 bottomSheet.state = BottomSheetBehavior.STATE_HIDDEN
 bottomSheet.setBottomSheetCallback(object : BottomSheetBehavior.BottomSheetCallback(){
            override fun onSlide(bottomSheet: View, slideOffset: Float) {

            }
            override fun onStateChanged(bottomSheet: View, newState: Int) {
                when(newState){
                    BottomSheetBehavior.STATE_COLLAPSED -> {
                        bottom_sheet_blur.visibility = View.VISIBLE
                        bottom_sheet_view.visibility = View.VISIBLE
                    }
                    BottomSheetBehavior.STATE_HIDDEN -> {
                        bottom_sheet_blur.visibility = View.INVISIBLE
                        bottom_sheet_view.visibility = View.INVISIBLE
                    }
                }
            }
        })
 ```
