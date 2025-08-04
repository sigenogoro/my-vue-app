# Vue.js のemit

## 概要
`emit`は、Vue.jsにおいて子コンポーネントから親コンポーネントにイベントを送信するためのメカニズムです。これにより、コンポーネント間で双方向のデータ通信が可能になります。

## 基本的な使い方

### 子コンポーネントでのemit
```vue
<template>
  <button @click="handleClick">クリックして親にメッセージを送信</button>
</template>

<script>
export default {
  emits: ['message'], // emitするイベントを宣言
  methods: {
    handleClick() {
      this.$emit('message', 'Hello from child!');
    }
  }
}
</script>
```

### 親コンポーネントでのイベント受信
```vue
<template>
  <div>
    <child-component @message="handleMessage" />
    <p>{{ receivedMessage }}</p>
  </div>
</template>

<script>
import ChildComponent from './ChildComponent.vue'

export default {
  components: {
    ChildComponent
  },
  data() {
    return {
      receivedMessage: ''
    }
  },
  methods: {
    handleMessage(message) {
      this.receivedMessage = message;
    }
  }
}
</script>
```

## Composition APIでの使い方

```vue
<template>
  <button @click="handleClick">送信</button>
</template>

<script setup>
const emit = defineEmits(['message']);

const handleClick = () => {
  emit('message', 'Hello from Composition API!');
};
</script>
```

## emitsオプション
コンポーネントが発行するカスタムイベントを明示的に宣言することを推奨します：

```javascript
export default {
  emits: {
    // バリデーションなし
    click: null,
    
    // バリデーションあり
    submit: (payload) => {
      // trueを返すとイベントが有効
      return payload.email && payload.password;
    }
  }
}
```

## 複数の引数を渡す
```javascript
// 子コンポーネント
this.$emit('update', id, name, email);

// 親コンポーネント
@update="(id, name, email) => handleUpdate(id, name, email)"
```

## v-modelとの連携
Vue 3では、v-modelは`modelValue`プロパティと`update:modelValue`イベントを使用します：

```vue
<!-- 子コンポーネント -->
<template>
  <input 
    :value="modelValue" 
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>

<script>
export default {
  props: ['modelValue'],
  emits: ['update:modelValue']
}
</script>
```

```vue
<!-- 親コンポーネント -->
<template>
  <custom-input v-model="text" />
</template>
```

## 注意点
- イベント名はケバブケース（kebab-case）を使用することを推奨
- `emits`オプションでイベントを宣言することで、コンポーネントの意図が明確になる
- 親コンポーネントでイベントリスナーを設定する際は、`@`または`v-on:`を使用