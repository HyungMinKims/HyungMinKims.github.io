---
title: "[android] static 변수의 값이 영구적으로 보존 되지 않은 이유"
categories:
- android
tag:
- android
- error check
toc: true 
toc_sticky: true
toc_label: "깃 허브 계정 꾸미기"
last_modified_at: 2022-07-05T17:37:43-05:00
author_profile: true
sidebar:
  nav: "docs"
date:   2022-07-04 12:00:00
lastmod : 2022-07-04 12:00:00
sitemap :
  changefreq : daily
  priority : 1.0
---
앱을 켜놓은 상태에서 다음 날 앱을 다시 실행하면 static 변수에 담긴 값들이 보존이 안되고 
사라진 오류를 한번 씩 본 적이 있을 겁니다. 오늘 이야기 해보고 싶은 내용은 **왜 보존이 안되고 해결방법이 무엇이 있는지** 
알아보도록 하겠습니다.

## 왜 보존 되지 않고 사라질까?
우리는 안드로이드 OS를 어느 곳에 많이 사용하고 있는지 생각을 해보십다.
<br> 단연히 스마트폰일 것 입니다.
<br><br>
스마트폰은 데스크탑에 비해서 메모리는 상당히 한정적입니다. 따라서 안드로이드 OS는 **계속 감시를 하면서 필요하지 않은 메모리를 회수**
를 합니다. 
<br>
<br>
어떤 앱을 실행시키고, 유저가 다른 앱으로 이동하거나 홈 화면으로 이동할 때(앱이 백그라운드 실행 상태가 될 때)
안드로이드 OS는 이들을 우선 정리 대상으로 설정합니다.
<br>
<br>
![image-center](/assets/post/2022-07-04-android-onStop-Static-error/lifecycle.png){: .align-center}

위 그림은 액티비티 생명주기(Activity Lifecycle) 입니다.
유저가 백그라운드로 나가서[**onStop**]렘이 부족한 상태가 되면 
App process killed가 작동되고 다시 유저가 포그라운드로 이동시키면 마지막 액티비티의 [**onCreate**] 부터 다시 시작하게 됩니다.

결론적으로 onStop 상태에서 렘이 부족하여 Static 변수의 값을 들고오는 경우가 발생하는데 이 떄 다시 앱을 실행 시 변수에 값이 없기 때문에 널포인트익셉션이 
발생하는 경우가 나타납니다. 그럼 값을 어떻게 보존을 할 지 생각을 해봅시다.

## 값을 보존하려면 어떻게?
### 내장메모리에 저장
영구적으로 데이터를 보존하려면 안드로이드 내장 메모리에 저장 하는 방법 밖에 없습니다.
<br> 즉 DataStore, SharedPreference, Room, SQLITE3 등 내장 메모리에 저장하는 기능을 구현하여 사용해야 합니다.

### 스플래시 화면으로 강제 이동
App process killed 발생 후 onCreate에서 static 값이 보존되어 있는지 체크하고 값이 소실 된 경우 
<br>
다시 Intent에 Top flag를 준 다음 강제 첫 화면으로 이동시키는 방법도 있습니다.


> 참조 [https://stackoverflow.com/questions/4797187/android-static-variable-null-on-low-memory](https://stackoverflow.com/questions/4797187/android-static-variable-null-on-low-memory)


