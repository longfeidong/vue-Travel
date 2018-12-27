<template>
  <div id="app">
    <!-- router-view首次渲染完页面后默认会缓存页面的请求, exclude可以设置不缓存的组件 -->
    <keep-alive exclude="Detail">
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
