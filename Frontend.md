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

### API

#### `Vue.set(target, key, value)`

- `{Object | Array} target`
- `{string | number} key`
- `{any} value`

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
