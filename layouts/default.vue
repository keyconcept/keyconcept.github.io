<template>
  <div>
    <client-only>
      <Header></Header>
      <Nuxt />
    </client-only>
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
