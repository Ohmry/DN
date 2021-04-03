# Vuejs에서 Render 함수를 이용한 Component 작성 방법

``` js
// ComponentTemplate.js
import Vue from 'vue'

export default Vue.component('component-template', {
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
