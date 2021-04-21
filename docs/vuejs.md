# Vuejs
  - [Vuejs에서 Render 함수를 이용한 Component 작성 방법](#vuejs에서-render-함수를-이용한-component-작성-방법)
  - [render 함수에서 data (), computed () 쓰는 방법](#render-함수에서-data--computed--쓰는-방법)
  - [render 함수에서 props 쓰는 방법](#render-함수에서-props-쓰는-방법)
  - [컴포넌트의 이름을 console.log로 찍는 방법](#컴포넌트의-이름을-consolelog로-찍는-방법)

## Vuejs에서 Render 함수를 이용한 Component 작성 방법

``` js
// ComponentTemplate.js
import Vue from 'vue'

export default Vue.component('component-template', {
  props: ['role'],
  data () {
    ...
  },
  computed: {
    isTest () {
      return ...
    }
  }
  return (h) {
    return h(
      'h1',     // html 태그
      {},       // Props
      'TEST"    // 하위 엘리멘트 (배열로 새로운 태그도 추가 가능)
    )
  }
})
```

``` js
// Parents Components
<template>
  <div>
    <component-template></component-template>
  </div>
</template>

<script>
import ComponentTemplate from './ComponentTemplate.js'
// 또는 const ComponentTemplate = require ('./ComponentTemplate.js).default

export default {
  name: 'parent-component',
  components: {
    ComponentTemplate
  }
}
</script>

<style>
...
</style>
```

## render 함수에서 data (), computed () 쓰는 방법
  - https://stackoverflow.com/questions/46910101/vuejs-how-to-access-computed-values-in-render-function

## render 함수에서 props 쓰는 방법
  - https://stackoverflow.com/questions/44013140/how-to-pass-props-to-class-using-vuejs-render-function

## 컴포넌트의 이름을 console.log로 찍는 방법
``` javascript
console.log(this.$options.name)

// 부모 컴포넌트의 이름을 찾는 경우
console.log(this.$parent.$options.name)
```