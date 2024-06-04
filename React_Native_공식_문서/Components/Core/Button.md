# 📱 Button

어떤 플랫폼에서든 잘 렌더링되어야 하는 기본 버튼 컴포넌트이다. 최소 수준의 커스터마이징을 지원한다.

이 버튼이 앱에 적합하지 않은 경우 [Pressable]()을 사용해 버튼을 만들 수 있다.

> Button 소스 코드 보러 가기

[Button.js](https://github.com/facebook/react-native/blob/main/packages/react-native/Libraries/Components/Button.js)

### Example Code

```jsx
<Button
  onPress={onPressLearnMore}
  title='Learn More'
  color='#841584'
  accessibilityLabel='Learn more about this purple button'
/>
```

## Reference

### Props

> 🌟**REQUIRED**🌟 `onPress`

- 사용자가 버튼을 누를 때 호출되는 핸들러 함수

|             TYPE              |
| :---------------------------: |
| `({nativeEvent: PressEvent})` |

> 🌟**REQUIRED**🌟 `title`

- 버튼 내부에 보여주기 위한 텍스트
- 👾 Android에서는 주어진 값이 대문자 형식으로 변환된다.

|   TYPE   |
| :------: |
| `string` |

> `accessibilityLabel`

- 시각 장애인을 위한 접근성 기능에 표시될 텍스트

|   TYPE   |
| :------: |
| `string` |

> `accessibilityLanguage` (🍎)

- 사용자가 요소와 상호작용할 때 스크린 리더기에 어떤 언어가 사용되어야 하는지를 나타내는 값
- [BCP 47 명세](https://www.rfc-editor.org/info/bcp47)를 따라야 한다.
- [iOS 문서](https://developer.apple.com/documentation/objectivec/nsobject/1615192-accessibilitylanguage)에서 더 자세히 알아볼 수 있다.

|   TYPE   |
| :------: |
| `string` |

> `accessibilityActions`

- 접근성 액션은 보조 기술이 구성 요소의 액션을 프로그래밍 방식으로 호출할 수 있도록 한다.
  - 스크린 리더기, 음성 명령 시스템 등의 보조 기술이 특정 사용자 인터페이스 컴포넌트의 동작을 프로그래밍 방식으로 실행할 수 있게 해준다.
  - 사용자가 직접 클릭하거나 조작하지 않아도 보조 기술이 구성 요소에 정의된 동작을 대신 수행할 수 있게 지원한다.
- `accessibilityActions` 속성에는 액션 객체 목록이 포함되어야 하며 각 액션 객체는 `name`과 `label` 필드를 포함해야 한다.
- 더 많은 정보를 원한다면 [접근성 가이드](https://reactnative.dev/docs/accessibility#accessibility-actions)를 참조하자.

|  TYPE   | REQUIRED |
| :-----: | :------: |
| `array` |    ❌    |

> `onAccessibilityAction`

- 사용자가 접근성 액션을 실행했을 때 호출된다.
- 이 함수의 유일한 인자는 수행할 작업의 이름이 포함된 이벤트이다.
- 더 많은 정보를 원한다면 [접근성 가이드](https://reactnative.dev/docs/accessibility#accessibility-actions)를 참조하자.

|    TYPE    | REQUIRED |
| :--------: | :------: |
| `function` |    ❌    |

> `color`

- 🍎: 텍스트의 색
- 👾: 버튼 배경색

|  TYPE   |              DEFAULT              |
| :-----: | :-------------------------------: |
| `color` | 🍎: `#007AFF` <br/> 👾: `#2196F3` |

> `disabled`

- `true`라면 이 컴포넌트에 대한 모든 상호작용이 비활성화된다.

|  TYPE  | DEFAULT |
| :----: | :-----: |
| `bool` | `false` |

> `hasTVPreferredFocus` (📺 TV)

- TV 환경에서 해당 버튼이 애플리케이션이 처음 시작될 때 기본적으로 포커스를 받도록 지정하는 속성

|  TYPE  | DEFAULT |
| :----: | :-----: |
| `bool` | `false` |

> `nextFocusDown` (👾, 📺)

- 사용자가 아래로 이동할 때 포커스를 받을 다음 뷰를 지정한다.

|   TYPE   |
| :------: |
| `number` |

> `nextFocusForward` (👾, 📺)

- 사용자가 앞으로 이동할 때 포커스를 받을 다음 뷰를 지정한다.

|   TYPE   |
| :------: |
| `number` |

> `nextFocusLeft` (👾, 📺)

- 사용자가 왼쪽으로 이동할 때 포커스를 받을 다음 뷰를 지정한다.

|   TYPE   |
| :------: |
| `number` |

> `nextFocusRight` (👾, 📺)

- 사용자가 오른쪽으로 이동할 때 포커스를 받을 다음 뷰를 지정한다.

|   TYPE   |
| :------: |
| `number` |

> `nextFocusUp` (👾, 📺)

- 사용자가 위로 이동할 때 포커스를 받을 다음 뷰를 지정한다.

|   TYPE   |
| :------: |
| `number` |

> `testId`

- e2e 테스트의 마지막에 이 뷰를 찾는 데 사용된다.

|   TYPE   |
| :------: |
| `string` |

> `touchSoundDisabled` (👾)

- `true`면 터치 시 시스템의 소리를 재생하지 않는다.

|   TYPE    | DEFAULT |
| :-------: | :-----: |
| `boolean` | `false` |
