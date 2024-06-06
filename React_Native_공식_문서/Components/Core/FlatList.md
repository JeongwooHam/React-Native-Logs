# 📱 FlatList

기본적이고 평면적인 리스트를 렌더링하기 위한 성능 좋은 인터페이스로, 다음과 같은 유용한 기능들을 지원한다:

- 완전한 크로스 플랫폼 지원
- 선택 가능한 가로 모드
- 리스트 항목이 사용자의 뷰포트에 나타나거나 사라질 때 호출되는 콜백함수를 구성할 수 있다.
- 헤더와 푸터, 구분자 지원
- 당겨서 새로 고침
- 스크롤 로딩
- ScrollToIndex 지원
- 다중 열 지원

더 많은 **구역**에 대한 지원이 필요하다면 [`<SectionList>`]()를 사용하자.

### Example Code

```js
<FlatList
  ItemSeparatorComponent={
    Platform.OS !== "android" &&
    (({ highlighted }) => (
      <View style={[style.separator, highlighted && { marginLeft: 0 }]} />
    ))
  }
  data={[{ title: "Title Text", key: "item1" }]}
  renderItem={({ item, index, separators }) => (
    <TouchableHighlight
      key={item.key}
      onPress={() => this._onPress(item)}
      onShowUnderlay={separators.highlight}
      onHideUnderlay={separators.unhighlight}
    >
      <View style={{ backgroundColor: "white" }}>
        <Text>{item.title}</Text>
      </View>
    </TouchableHighlight>
  )}
/>
```

## Props

### **VirtualizedList Props**

- VirtualizedList Props를 상속한다.

### 🌟**REQUIRED**🌟 `renderItem`

|    TYPE    |
| :--------: |
| `function` |

- `data`에서 아이템을 가져와 목록에 렌더링한다.
- 추가 메타데이터(예: `index`)가 필요한 경우 제공된다.
- `separators.updateProps` 함수도 제공되어, 리스트 항목 사이의 구분자에 원하는 속성을 설정할 수 있다.
  - `highlight`와 `unhighlight`(`boolean` 속성을 설정함)로 충분하지 않은 경우 `updateProps`를 사용해 `leading` 구분자 또는 `trailing` 구분자의 렌더링을 속성을 변경할 수 있다.

```js
renderItem({
  item: ItemT,
  index: number,
  separators: {
    highlight: () => void;
    unhighlight: () => void;
    updateProps: (select: 'leading' | 'trailing', newProps: any) => void;
  }
}): JSX.Element;
```

- **item (Object)**: `data`에서 렌더링 될 아이템
- **index (number)**: `data` 배열에서 이 아이템에 해당하는 인덱스
- **seperators (Object)**
  - `highlight` (Function)
  - `unhighlight` (Function)
  - `updateProps` (Function)
    - `select` (`leading`과 `trailing`으로 구성된 enum)
    - `newProps` (Object)

### 🌟**REQUIRED**🌟 `data`

|   TYPE    |
| :-------: |
| ArrayLike |

- 렌더링할 항목의 배열(또는 이와 유사한 목록)
- 다른 데이터 타입의 경우 `VirtualizedList`를 직접적으로 타겟팅하여 사용할 수 있다.

### `ItemSeperatorComponent`

|             TYPE             |
| :--------------------------: |
| component, function, element |

- 각각의 아이템 사이에 렌더링되지만 맨 위나 맨 아래에는 렌더링되지 않는다.
- 기본적으로 `highlighted`와 `leadingItem` prop이 제공된다.
- `renderItem`은 `seperators.highlight`와 `unhighlight`를 제공하여 `highlighted` prop을 업데이트할 수 있다.
- `seperators.updateProps`를 사용해 직접 임의의 prop을 추가할 수도 있다.
- 리액트 컴포넌트(`Component`) 또는 리액트 요소(`<Component/>`)가 될 수 있다.

### `ListEmptyComponent`

|        TYPE        |
| :----------------: |
| component, element |

- 배열이 비어있을 경우 렌더링 된다.
- 리액트 컴포넌트 또는 리액트 요소가 될 수 있다.

### `ListFooterComponent`

|        TYPE        |
| :----------------: |
| component, element |

- 모든 항목의 맨 아래에 렌더링 된다.
- 리액트 컴포넌트 또는 리액트 요소가 될 수 있다.

### `ListFooterComponentStyle`

|       TYPE       |
| :--------------: |
| [`View Style`]() |

- `ListFooterComponent`의 내부 `View`를 스타일링한다.

### `ListHeaderComponent`

|        TYPE        |
| :----------------: |
| component, element |

- 모든 항목의 제일 위에 렌더링 된다.
- 리액트 컴포넌트 또는 리액트 요소가 될 수 있다.

### `ListHeaderComponentStyle`

|       TYPE       |
| :--------------: |
| [`View Style`]() |

- `ListHeaderComponent`의 내부 `View`를 스타일링한다.

### `columnWrapperStyle`

|       TYPE       |
| :--------------: |
| [`View Style`]() |

- `numColumns > 1`일 때 생성되는 다중 항목 행에 대한 선택적인 사용자 지정 스타일

### `extraData`

| TYPE  |
| :---: |
| `any` |

- 목록에 리렌더링하도록 지시하기 위한 마커 속성이다. (`PureComponent`를 구현하기 때문이다.)
- `renderItem`, 헤더, 푸터 등의 함수가 `data` prop`의 외부에 의존하는 경우 여기에 붙여서 불변하게 처리해야 한다.

### `getItemLayout`

|   TYPE   |
| :------: |
| function |

- 항목의 크기(높이, 너비)를 미리 알고 있는 경우 동적 콘텐츠의 측정을 건너뛸 수 있게 하는 선택적 옵션 최적화이다.

```ts
(data, index) => {length: number, offset: number, index: number}
```

- 수백 개의 항목이 있는 목록의 경우 이 속성을 추가하면 성능이 크게 향상될 수 있다.
- `ItemSeperatorComponent`를 지정하는 경우 offset 계산에 구분자의 길이(높이, 너비)를 포함해야 한다.

### `horizontal`

|   TYPE    |
| :-------: |
| `boolean` |

- `true`일 경우, 항목을 나란히 세로로 쌓는 대신 가로로 위치하게 렌더링한다.

### `initialNumToRender`

|   TYPE   | DEFAULT |
| :------: | :-----: |
| `number` |  `10`   |

- 초기 배치에서 렌더링할 아이템의 수를 결정한다.
- 화면을 채우기 충분해야 하지만 그 이상이면 안 된다.
  - scroll-to-top 동작의 인지 성능을 개선하기 위해 화면을 넘어간 항목들은 창 렌더링의 일부로 간주되어 언마운트 되지 않는다.

### `initialScrollIndex`

|   TYPE   |
| :------: |
| `number` |

- 첫 번째 항목과 함께 맨 위에서부터 시작하는 대신 시작할 인덱스를 결정한다.
- 첫 번째 `initialNumToRender` 아이템을 항상 렌더링하고 이 초기 인덱스에서 시작하는 항목을 즉시 렌더링함으로써 scroll-to-top 최적화를 비활성화한다.
- `getItemLayout`이 구현되어야 한다.

### `inverted`

|   TYPE    |
| :-------: |
| `boolean` |

- 스크롤의 방향을 뒤집는다.
- `-1`의 스케일 변환을 사용한다.

### `keyExtractor`

|   TYPE   |
| :------: |
| function |

- 특정한 인덱스에서 주어진 항목에 대한 특별한 키를 추출하기 위해 사용된다.
- 키는 캐싱에 사용되며 아이템 재나열을 추적하는 리액트 키로 사용된다.
- 기본 extractor는 `item.key`를 확인하고 `item.id`를 확인한 뒤 리액트처럼 인덱스를 사용한다.

```ts
(item: ItemT, index: number) => string;
```

### `numColumns`

|   TYPE   |
| :------: |
| `number` |

- 다중 열은 `horizontal = {false}`로만 렌더링될 수 있으며 `flexWrap` 레이아웃처럼 지그재그로 렌더링 된다.
- 항목들의 높이는 모두 같아야 하며 벽돌식 레이아웃은 지원되지 않는다.

### `viewabilityConfigCallbackPairs`

|                  TYPE                  |
| :------------------------------------: |
| `ViewabilityConfigCallbackPair`의 배열 |

- `ViewabilityConfig`/`onViewableItemsChanged` 페어들의 목록.
- 상응하는 `ViewabilityConfig`의 조건이 맞으면 특정한 `onViewableItemsChanged`가 호출된다.

## Methods

### `flashScrollIndicators( )`

- 스크롤 표시기를 순간적으로 보여준다.

### `getNativeScrollRef( )`

```ts
getNativeScrollRef(): React.ElementRef<typeof ScrollViewComponent>
```

- 기본 스크롤 컴포넌트에 대한 참조를 제공한다.

### `getScrollResponder( )`

```ts
getScrollResponder(): ScrollResponderMixin
```

- 기본 스크롤 응답자에 대한 핸들링을 제공한다.

### `getScrollableNode( )`

```ts
getScrollableNode(): any
```

- 기본 스크롤 노드에 대한 핸들링을 제공한다.

### `scrollToEnd( )`

```ts
scrollToEnd(params?: {animated?: boolean})
```

- 콘텐츠의 마지막으로 스크롤한다. `getItemLayout` prop을 사용하지 않으면 불안정할 수 있다.

> Parameters

|   NAME   |   TYPE   |
| :------: | :------: |
| `params` | `object` |

- **animated (boolean)**: 스크롤 시 목록에 애니메이션이 적용되어야 하는지에 대해 결정한다. 기본값은 `true`

### `scrollToIndex( )`

```ts
scrollToIndex: (params: {
  index: number;
  animated?: boolean;
  viewOffset?: number;
  viewPosition?: number;
})
```

- 지정된 인덱스의 항목으로 스크롤한다. 가시 영역에서 `viewPosition` 0이 맨 위에, 1이 맨 아래에, 0.5가 중앙에 위치하도록 항목을 스크롤한다.
- ✔️ `getItemLayout` prop을 명시하지 않으면 렌더링 창 밖의 위치로 스크롤할 수 없다.

> Parameters (🌟**REQUIRED**🌟)

|   NAME   |   TYPE   |
| :------: | :------: |
| `params` | `object` |

- **animated (boolean)**: 스크롤 시 목록에 애니메이션이 적용되어야 하는지에 대해 결정한다. 기본값은 `true`
- **index (number)**: 스크롤 할 인덱스. **필수 항목**이다.
- **viewOffset (number)**: 최종 목표 위치를 offset하기 위한 고정 픽셀 값이다.
- **viewPosition (number)**: 0이면 인덱스로 지정한 항목이 맨 위에, 1이면 맨 아래에, 0.5면 중앙에 배치된다.

### `scrollToItem( )`

```ts
scrollToItem: (params: {
  animated?: boolean;
  item: Item;
  viewPosition?: number;
})
```

- 데이터를 선형적으로 스캔하도록 요구한다. 가능하다면 `scrollToIndex`를 대신 사용하자.
- ✔️ `getItemLayout` prop을 명시하지 않으면 렌더링 창 밖의 위치로 스크롤할 수 없다.

> Parameters (🌟**REQUIRED**🌟)

|   NAME   |   TYPE   |
| :------: | :------: |
| `params` | `object` |

- **animated (boolean)**: 스크롤 시 목록에 애니메이션이 적용되어야 하는지에 대해 결정한다. 기본값은 `true`
- **item (object)**: 스크롤할 아이템. **필수 항목**이다.
- **viewPosition (number)**

### `scrollToOffset( )`

```ts
scrollToOffset: (params: {
  animated?: boolean;
  offset: number;
})
```

- 목록에서 특정 콘텐츠의 픽셀 offset으로 스크롤한다.

> Parameters (🌟**REQUIRED**🌟)

|   NAME   |   TYPE   |
| :------: | :------: |
| `params` | `object` |

- **animated (boolean)**: 스크롤 시 목록에 애니메이션이 적용되어야 하는지에 대해 결정한다. 기본값은 `true`
- **offset (number)**: 스크롤할 offset. `horizontal`이 참이면, offset은 x축에 대한 값이고 아니라면 y축에 대한 값이다. **필수 항목**이다.
