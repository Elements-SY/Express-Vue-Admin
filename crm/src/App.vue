<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script>
export default {
  name: "App",
};
</script>
<style lang="scss">
ul {
  padding: 0;
}
li {
  list-style: none;
}
html,
body {
  background-color: rgb(240, 242, 245);
}
.atooltip.el-tooltip__popper[x-placement^="top"] .popper__arrow {
  border-top-color: pink;
}
.atooltip.el-tooltip__popper[x-placement^="top"] .popper__arrow:after {
  border-top-color: pink;
}
.atooltip {
  background: pink !important;
}
</style>
