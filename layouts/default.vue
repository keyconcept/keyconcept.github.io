<template>
  <div>
    <Header></Header>
    <Nuxt />
  </div>
</template>
<script>
import Header from '~/components/Header'
export default {
  components: { Header },
}
</script>
<style>
body {
  background-color: black;
}
</style>
