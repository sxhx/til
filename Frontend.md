# Frontend

## Ajax

### Axios

#### 헤더 정보는 제일 마지막에 넣는다

```js
axios({
  method: post,
  data: {},
  headers: {}
});
```

## Vue

### Vue API

#### `Vue.set(target, key, value)`

- `{Object | Array} target`
- `{string | number} key`
- `{any} value`

### Vuex

#### 기본 요소들

- State
  - 리액트의 state 와 같다.
- Getters
  - 로컬 컴포넌트의 computed 속성과 같다고 생각하면 쉽다.
- Mutations
  - state 를 변경하기 위한 함수들.
- Actions
  - mutation 함수들을 commit 하기 위한 함수들.
  - 여기서 비동기 처리를 하자.

#### `actions`에서 다른 `action` 부르려면?

```js
someAction({ dispatch }) { // dispatch를 param으로 받을 수 있다.
  // ...
  dispatch('anotherAction')
};
```

#### 'getters'에서 다른 'getter'를 부르려면?

```js
export default {
  someGetter: (state, getters) => {
    getters.anotherGetter;
  };
}
```

#### Form 에서 `v-model`을 사용하려면?

```html
<input v-model="message">
```

```js
// ...
computed: {
  message: {
    get () {
      return this.$store.state.obj.message
    },
    set (value) {
      this.$store.commit('updateMessage', value)
    }
  }
}
```

### 자잘한 것들

> #### form element 기본 동작 막기:
>
> `@keyup(down/press).enter.prevent`

> #### 한글이 중복 입력 될 때:
>
> `@keypress` 를 사용하니까 해결됐다.

> #### 클릭 이벤트가 중복 발생할 때:
>
> `@click.stop`

> #### Vue 만지다가 `Uncaught (in promise) TypeError`를 만났다:
>
> 어딘가 async 처리가 필요한 상황인 것으로 추정됨.
