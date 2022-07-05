---
title: "[android] 안드로이드 앱 권장 아키텍처 알아보자. part.1"
categories:
- android
tag:
- android
toc: true
toc_sticky: true
toc_label: "앱 아키텍처"
---
현재 안드로이드에서 권장하는 앱 아키텍처를 알아보도록 하겠습니다. 
> 참고: [https://developer.android.com/jetpack/guide?hl=ko](https://developer.android.com/jetpack/guide?hl=ko)

## 아키텍처란
우선 들어가기 전 아키텍처가 무엇 인 지 부터 설명을 하겠습니다. 아키텍처에 종류는 여러가지가 있습니다. 여러가지 중 소프트웨어에서만 사용하는 
<br>
소프트웨어 아키텍처가 있습니다. 소프트웨어 아키텍처는 **소프트웨어의 골격이 되는 기본구조로서 소프트웨어의 구조를 단계별로 설계하고 구축하는 방법**
<br>
입니다.


## 1. 일반 아키텍처 원칙
### 관심사 분리
초보자들 가장 많이 하는 실수가 `activity` 와 `fragment`에 모든 코드를 작성하는 실수가 있습니다. `actvity`와 `fragment`는 UI 및 운영체제 상호작용을
<br>
처리하는 로직만 포함해야 합니다. 이러한 클래스를 최대한 가볍게 유지하여 구성요소 수명 주기와 관련된 많은 문제를 피하고 그러한 클래스의 테스트 가능성을
<br>
개선 할 수 있습니다.

## 2. 권장 앱 아키텍처
안드로이드에서는 사용자에게 보여지는 화면 (UI), 사용자 요청에 따라 필요한 정보 (Data), 화면과 데이터의 연결 다리 (Domain) 크게 3개의 영역으로 나눌 수
<br>
있습니다. 안드로이드에서는 이 3가지 영역으로 나누어서 관리하도록 권장을 했습니다.
<br>
![image-center](/assets/post/2022-07-05-app-recommend-Architecture/madarchoverview.png){: .align-center}
<p style="text-align: center; font-size: 12px">일반적인 앱 아키텍쳐 다이어그램</p>
<br>

3 가지를 영역을 **자동차**로 비교하여 설명 드리겠습니다.

### UI Layer
![image-center](/assets/post/2022-07-05-app-recommend-Architecture/mad-arch-overview-ui.png){: .align-center}
<br>
UI Layer은 유저한테 보여지는 화면들이라고 하시면 됩니다. 즉 **자동차 그 자체** 라고 생각 하시면 됩니다.
<br>
UI Layer에서는 크게 두 가지로 구성됩니다. 
- UI elements(컴포넌트)
- state holders(뷰 모델)

> UI elements: **자동차의 바퀴, 색상** <br>
> state holders: **자동차의 색상 값**

### Domain Layer
![image-center](/assets/post/2022-07-05-app-recommend-Architecture/mad-arch-overview-domain.png){: .align-center}
<br>
Domain Layer은 `UI Layer`와 `Data Layer`를 선택하여 사용하는 레이어라고 생각하시면 됩니다.
<br>
복잡한 비즈니스 로직, 또는 여러 ViewModel에서 재사용되는 간단한 비즈니스 로직의 캡슐화를 담당하고 있습니다.
<br>
앱의 클래스는 올바른 작동을 위해 다른 클래스에 종속됩니다. 특정 클래스의 종속 항목을 수집하는 데 다음 디자인 패턴 중 하나를 사용할 수 있습니다.

- 종속 항목 주입(DI): 종속 항목 주입을 사용하면 클래스가 자신의 종속 항목을 구성할 필요 없이 종속 항목을 정의할 수 있습니다. 런타임 시 다른 클래스가 이 종속 항목을 제공해야 합니다.


- 서비스 로케이터: 서비스 로케이터 패턴은 클래스가 자신의 종속 항목을 구성하는 대신 종속 항목을 가져올 수 있는 레지스트리를 제공합니다.
이 패턴은 코드를 중복하거나 복잡성을 추가하지 않아도 종속 항목을 관리하기 위한 명확한 패턴을 제공하므로 코드를 확장할 수 있습니다. 또한 이러한 패턴을 사용하면 테스트와 프로덕션 구현 간에 신속하게 전환할 수 있습니다.

**종속 항목 삽입 패턴을 따르고 Android 앱에서 Hilt 라이브러리를 사용하는 것이 좋습니다.**
> Domain Layer: **자동차 색상 데이터 연결 다리** 

### Data Layer
![image-center](/assets/post/2022-07-05-app-recommend-Architecture/mad-arch-overview-data.png){: .align-center}
<br>
앱의 데이터 레이어에는 비즈니스 로직이 포함되어 있습니다. 비즈니스 로직은 앱에 가치를 부여하는 요소로, 앱의 데이터 생성, 저장, 변경 방식을 결정하는 규칙으로 구성됩니다.
<br>
각 데이터 소스 클래스는 파일, 네트워크 소스, 로컬 데이터베이스 같은 하나의 데이터 소스만 사용해야 합니다. 데이터 소스 클래스는 데이터 작업을 위해 애플리케이션과 시스템 간의 가교 역할을 합니다.
> Data Layer: **자동차 선택 가능한 색상 값들**