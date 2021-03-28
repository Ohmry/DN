# Electron에서 프레임이 없는 창을 만들 때, 드래그 기능 추가하는 방법
``` html
<template>
  <div class='container'>
    <section class='titlebar'>
      <button class='window-controls'>Minimize</button>
      <button class='window-controls'>Maximize</button>
      <button class='window-controls'>Close</button>
    </section>
  </div>
</template>

...

<style scoped>
/** 이걸 추가해서 창이 드래그될 수 있게 할 수 있다. */
.container { -webkit-app-region: drag; }
/** 버튼들에도 drag 옵션이 들어갈 경우 클릭이 안되므로 버튼은 제외한다. */
.container > .titlebar > button {
  -webkit-app-region: no-drag;
}
</style>
```