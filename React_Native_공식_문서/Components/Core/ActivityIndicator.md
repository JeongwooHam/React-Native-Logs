# 📱 ActivityIndicator

원형의 로딩 indicator를 보여준다.

![image](https://github.com/JeongwooHam/FE_Study_Logs/assets/123251211/b2f95d73-0eb4-4add-8521-756a5a13e18a)

### Example Code

```jsx
import React from "react";
import { ActivityIndicator, StyleSheet, View } from "react-native";

const App = () => (
  <View style={[styles.container, styles.horizontal]}>
    <ActivityIndicator />
    <ActivityIndicator size='large' />
    <ActivityIndicator size='small' color='#0000ff' />
    <ActivityIndicator size='large' color='#00ff00' />
  </View>
);

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: "center",
  },
  horizontal: {
    flexDirection: "row",
    justifyContent: "space-around",
    padding: 10,
  },
});

export default App;
```

## Reference

### Props

> **View Props**

- View Props를 상속한다.

> `animating`

- indicator를 보여줄지(`true`) 혹은 숨길지(`false`)를 결정한다.

|  TYPE  | DEFAULT |
| :----: | :-----: |
| `bool` | `true`  |

> `color`

- spinner의 전경 색

|  TYPE   |                                  DEFAULT                                   |
| :-----: | :------------------------------------------------------------------------: |
| `color` | **👾 Android**: `null` (시스템 강조 기본 색상) <br/> **🍎 iOS**: `#999999` |

> `hideWhenStopped` (🍎 iOS)

- 애니메이션을 적용하지 않을 때 indicator를 숨길 것인지

|  TYPE  | DEFAULT |
| :----: | :-----: |
| `bool` | `true`  |

> `size`

- indicator의 크기

|           TYPE           | DEFAULT |
| :----------------------: | :-----: |
| `enum('small', 'large')` | `small` |
|  `number` (👾 Android)   | `small` |
