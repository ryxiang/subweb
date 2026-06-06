<template>
  <div id="app">
    <router-view />
    <dialog-view v-if="$store.state.app.dialog.active"></dialog-view>
  </div>
</template>

<script>
export default {
  name: 'app',
};
</script>

<style>
@import '@/assets/theme.css';
@import 'element-plus/theme-chalk/index.css';
</style>
