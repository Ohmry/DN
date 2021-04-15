# Vuejs에서 컴포넌트의 이름을 console.log로 찍는 방법
``` javascript
console.log(this.$options.name)

// 부모 컴포넌트의 이름을 찾는 경우
console.log(this.$parent.$options.name)
```