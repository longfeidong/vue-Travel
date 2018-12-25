<template>
  <div id="app">
    <!-- router-view首次渲染完页面后默认会缓存页面的请求 -->
    <keep-alive>
      <router-view/>
    </keep-alive>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style></style>
