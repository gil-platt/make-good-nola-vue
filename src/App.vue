<template>
  <div id="root">
    <HeaderBar />
    <router-view />
  </div>
</template>

<script>
import HeaderBar from "./components/header-bar/header-bar";
export default {
  name: 'App',
  components: {
    HeaderBar
  }
}
</script>
