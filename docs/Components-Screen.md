# Screen Component

[Back to all components](./Components.md)

This is a component that renders a screen. It is used to wrap your entire screen, and handles scrolling, [safe areas](https://reactnavigation.org/docs/handling-safe-area/), and keyboard avoiding behavior.

```tsx
<Screen preset="scroll">
  <Header headerTitle="screen" />
  // ... content here ...
</Screen>
```

## Props

### `children`

As the `Screen` component is a top level wrapper component, it is expected that you will pass in your screen's content as children.

```tsx
<Screen preset="scroll">
  <Header headerTitle="screen" />
  // ... content here ...
</Screen>
```

### `style`

The `style` prop is an optional `StyleProp<ViewStyle>` object that applies to the outer `View` or `SafeAreaView` component (depending on what is passed to `safeAreaEdges`). This is useful for applying styles to the outermost component, such as `margin` and `padding`.

```tsx
<Screen style={{ margin: 10, padding: 10 }}>
  <Header headerTitle="screen" />
  // ... content here ...
</Screen>
```

### `contentContainerStyle`

The `contentContainerStyle` prop is an optional `StyleProp<ViewStyle>` object that applies to the inner `View` component that wraps the `children`. This is useful for applying styles to the innermost component, such as `margin` and `padding`.

```tsx
<Screen contentContainerStyle={{ margin: 10 }}>
  <Header headerTitle="screen" />
  // ... content here ...
</Screen>
```

### `safeAreaEdges`

The `safeAreaEdges` prop is an an array of `SafeAreaEdges` that determines which edges of the screen should be considered safe areas. This is useful for handling the notch on iPhone X and other devices. The default value is `["top"]`.

```tsx
<Screen safeAreaEdges={["top", "bottom"]}>
  <Header headerTitle="screen" />
  // ... content here ...
</Screen>
```

### `backgroundColor`

The `backgroundColor` prop is an optional `string` that determines the background color of the outer wrapper component (either a `View` or `SafeAreaView`, depending on whether or not `safeAreaEdges` is empty). The default value is `colors.background`.

```tsx
<Screen backgroundColor="red">
  <Header headerTitle="screen" />
  // ... content here ...
</Screen>
```

### `statusBarStyle`

The `statusBarStyle` prop is a prop that determines the style of the status bar. It can be either `"light"` or `"dark"`. The default value is `"dark"`.

```tsx
<Screen statusBarStyle="light">
  <Header headerTitle="screen" />
  // ... content here ...
</Screen>
```

### `keyboardOffset`

The `keyboardOffset` prop is an optional `number` that determines the offset of the keyboard when it is shown. It is passed to the `keyboardVerticalOffset` of the `KeyboardAvoidingView`. The default value is `0`.

```tsx
<Screen keyboardOffset={10}>
  <Header headerTitle="screen" />
  // ... content here ...
</Screen>
```

### `SafeAreaViewProps`

The `SafeAreaViewProps` prop is an object that is passed as props to the [`SafeAreaView`](https://github.com/th3rdwave/react-native-safe-area-context#safeareaview).

```tsx
<Screen SafeAreaViewProps={{ padding: 10 }}>
  <Header headerTitle="screen" />
  // ... content here ...
</Screen>
```

### `StatusBarProps`

The `StatusBarProps` prop is an object that is passed as props to the `expo-status-bar` [`StatusBar`](https://docs.expo.io/versions/latest/sdk/status-bar/) component.

```tsx
<Screen StatusBarProps={{ animated: false }}>
  <Header headerTitle="screen" />
  // ... content here ...
</Screen>
```

### `KeyboardAvoidingViewProps`

The `KeyboardAvoidingViewProps` prop is an object that is passed as props to the [`KeyboardAvoidingView`](https://reactnative.dev/docs/keyboardavoidingview).

```tsx
<Screen KeyboardAvoidingViewProps={{ behavior: "padding" }}>
  <Header headerTitle="screen" />
  // ... content here ...
</Screen>
```

### `preset`

The `preset` prop is an optional enum that applies to the outer `KeyboardAvoidingView` component. The predefined presets with ignite deal with different use cases for scroll behavior and keyboard avoiding behavior. It defaults to `scroll` behavior if not set.

The predefined presets are:

- `scroll` - A preset that applies a scroll behavior to the screen. This is useful for forms or other screens which require a keyboard.
- `fixed` - A preset that applies a fixed behavior to the screen. i.e. The screen will not scroll. This is useful if you have a component such as a `FlashList` that has its own scrolling behavior.
- `auto` - A preset that applies an automatic behavior to the screen. i.e. The screen will scroll if the content is larger than the screen, but not otherwise.

```tsx
<Screen preset="scroll">
  <Header headerTitle="screen" />
  // ... content here ...
</Screen>
```

### `keyboardShouldPersistTaps`

The `keyboardShouldPersistTaps` optional prop is a enum that determines if the keyboard should persist taps. It defaults to `"handled"`. This only applies for the `scroll` preset, because it is passed into the React Native [`ScrollView`](https://facebook.github.io/react-native/docs/scrollview.html) component under its `keyboardShouldPersistTaps` prop.

The valid values for this prop are: `"handled"`, `"always"`,and `"never"`.

```tsx
<Screen preset="scroll" keyboardShouldPersistTaps="never">
  <Header headerTitle="screen" />
  // ... content here ...
</Screen>
```

### `ScrollViewProps`

The `ScrollViewProps` prop is an object that is passed as props to the React Native [`ScrollView`](https://facebook.github.io/react-native/docs/scrollview.html) component. This only applies for the `scroll` preset.

```tsx
<Screen preset="scroll" ScrollViewProps={{ contentContainerStyle: { padding: 10 } }}>
  <Header headerTitle="screen" />
  // ... content here ...
</Screen>
```

### `scrollEnabledToggleThreshold`

The `scrollEnabledToggleThreshold` prop is an optional `number` that determines the threshold at which the `scrollEnabled` prop of the `ScrollView` is toggled. This only applies for the `auto` preset. The default value is `{ percent: 0.92 }`. You can pass a point value in lieu of a percentage, e.g. `{ point: 100 }` will enable scrolling when the scroll view height is less than 100 points larger than the scroll view content height.

```tsx
<Screen preset="scroll" scrollEnabledToggleThreshold={{ percent: 0.95 }}>
  <Header headerTitle="screen" />
  // ... content here ...
</Screen>
```
