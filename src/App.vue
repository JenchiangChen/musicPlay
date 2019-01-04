<template>
  <div id="app">
    <m-header></m-header>
    <Navigation></Navigation>
    <keep-alive>
      <router-view></router-view>
    </keep-alive>
  </div>
</template>
<script>
  import MHeader from 'components/m-header/m-header'
  import Navigation from 'components/navigation/navigation'
export default {
  name: 'App',
  components: {
    MHeader,
    Navigation
  }
}
</script>

<style>
</style>
