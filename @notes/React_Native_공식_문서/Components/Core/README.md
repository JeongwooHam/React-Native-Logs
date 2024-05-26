# Core Components and APIs

React Native는 다양한 내장 [코어 컴포넌트](https://github.com/JeongwooHam/React-Native-Logs/blob/master/%40notes/React_Native_%EA%B3%B5%EC%8B%9D_%EB%AC%B8%EC%84%9C/Guides/01.%20The%20Basics/02.%20Core%20Components%20and%20Native%20Components.md)를 제공한다.

> 어디서부터 살펴봐야 할지 모르겠다면?

- 기본 컴포넌트들
- 사용자 인터페이스
- 리스트뷰
- Android 특화 컴포넌트와 API
- iOS 특화 컴포넌트와 API
- 기타

<br/>

React Native에 번들링된 컴포넌트와 API에 국한되지 않고 더 많은 라이브러리를 찾고 싶다면 [이 가이드](https://reactnative.dev/docs/libraries#finding-libraries)를 참조하면 된다.

### 💡 기본 컴포넌트들

대부분의 앱은 이러한 기본 컴포넌트 중 하나 이상을 사용하게 된다.

|  Component   | Description                                                                |
| :----------: | :------------------------------------------------------------------------- |
|    `View`    | UI를 구축함에 있어 가장 근본적인 컴포넌트                                  |
|    `Text`    | 텍스트를 표시하는 컴포넌트                                                 |
|   `Image`    | 이미지를 표시하는 컴포넌트                                                 |
| `TextInput`  | 키보드를 통해 앱에 텍스트를 입력하는 컴포넌트                              |
| `ScrollView` | 여러 컴포넌트와 `View`를 보여줄 수 있는 스크롤 가능한 컨테이너를 제공한다. |
| `StyleSheet` | CSS 스타일시트와 비슷한 추상화 계층을 제공한다.                            |

### 💡 사용자 인터페이스

이 공통 사용자 인터페이스 컨트롤은 모든 플랫폼에서 렌더링 된다.

| Component | Description                                                              |
| :-------: | :----------------------------------------------------------------------- |
| `Button`  | 어떤 플랫폼에서든 잘 렌더링 되는 터치를 처리하기 위한 기본 버튼 컴포넌트 |
| `Switch`  | `boolean` 타입의 입력값을 렌더링한다.                                    |

### 💡 리스트뷰

가장 기본적인 `ScrollView`와 달리 아래의 리스트뷰 컴포넌트들은 현재 화면에 보여지는 요소들만 렌더링한다.
이는 긴 데이터 목록을 표시할 때 탁월한 성능을 발휘한다.

|   Component   | Description                                             |
| :-----------: | :------------------------------------------------------ |
|  `FlatList`   | 스크롤 가능한 목록을 성능 좋게 렌더링하기 위한 컴포넌트 |
| `SectionList` | `FlatList`와 비슷하지만 구역화된 목록을 위한 컴포넌트   |

### 💡 Android 특화 컴포넌트와 API

아래의 다양한 컴포넌트들은 Android 클래스에서 주로 사용되는 wrapper를 제공한다.

|       Component       | Description                                                                                                          |
| :-------------------: | :------------------------------------------------------------------------------------------------------------------- |
|     `BackHandler`     | 뒤로 가기를 위한 하드웨어 버튼 클릭을 감지한다.                                                                      |
| `DrawerLayoutAndroid` | Android에서 Drawer 레이아웃을 렌더링한다.                                                                            |
| `PermissionsAndroid`  | [Android M](https://www.android.com/intl/ko_kr/versions/marshmallow-6-0/)에 도입된 권한 모델에 대한 접근을 제공한다. |
|    `ToastAndroid`     | Android 토스트 알림을 생성한다.                                                                                      |

### 💡 iOS 특화 컴포넌트와 API

아래의 다양한 컴포넌트들은 [UIKit](https://developer.apple.com/documentation/uikit) 클래스에서 주로 사용되는 wrapper를 제공한다.

|    Component     | Description                                        |
| :--------------: | :------------------------------------------------- |
| `ActionSheetIOS` | iOS의 액션 시트 또는 공유 시트를 보여주기 위한 API |

### 💡 기타

이 컴포넌트들은 특정 앱에서 유용할 것이다.

|       Component        | Description                                                                     |
| :--------------------: | :------------------------------------------------------------------------------ |
|  `ActivityIndicator`   | 원형 로딩 indicator를 보여준다.                                                 |
|        `Alert`         | 지정된 제목과 메세지가 포함된 알림 대화 상자를 보여준다.                        |
|       `Animated`       | 구현하고 유지하지 쉬운 유동적이고 강력한 애니메이션을 생성할 수 있는 라이브러리 |
|      `Dimensions`      | 기기의 치수를 가져오기 위한 인터페이스를 제공한다.                              |
| `KeyboardAvoidingView` | 가상의 키보드가 방해가 되지 않도록 자동으로 이동시키는 `View`를 제공한다.       |
|       `Linking`        | 수신 및 발신 앱 링크와 상호작용할 수 있는 일반적인 인터페이스를 제공한다.       |
|        `Modal`         | 둘러싸는 `View` 위헤 콘텐츠를 표시하기 위한 간단한 방법을 제공한다.             |
|      `PixelRatio`      | 기기의 픽셀 밀도에 대한 접근을 제공한다.                                        |
|    `RefreshControl`    | `ScrollView` 내부에 사용되어 끌어 당겨 새로고침을 할 수 있는 기능을 제공한다.   |
|      `StatusBar`       | 앱의 상태 표시줄을 제어하는 컴포넌트                                            |
