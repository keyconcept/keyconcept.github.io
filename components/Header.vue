<template lang="html">
  <b-navbar
    toggleable="lg"
    type="dark"
    :sticky="true"
    fixed
    class="nn-bg-brown nn-navbar nn-text-light"
  >
    <b-navbar-brand href="/" style="padding: 0; margin: 0; height: 40px">
      <picture>
        <source srcset="/kc-logo.png" type="image/png" />
        <b-img src="/kc-logo.png" style="height: 40px"> </b-img>
      </picture>
    </b-navbar-brand>
    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav> </b-navbar-nav>
      <b-navbar-nav class="ml-auto">
        <b-navbar-nav right>
          <b-nav-item href="/">Home</b-nav-item>
          <b-nav-item href="/contact">Contact us</b-nav-item>
          <b-nav-item
            href="https://www.facebook.com/Keyconcept-511244502730746"
            target="_blank"
          >
            <b-icon-facebook></b-icon-facebook>
          </b-nav-item>
        </b-navbar-nav>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</template>

<script>
export default {
  data() {
    return { visible: false }
  },
}
</script>

<style lang="css" scoped>
a {
  color: white !important;
}
</style>
