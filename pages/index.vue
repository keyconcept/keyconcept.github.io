<template lang="html">
  <div class="">
    <b-carousel
      :interval="4000"
      controls
      indicators
      background="#ababab"
      class="kc-carousel"
    >
      <picture v-for="project in projects" :key="project.id">
        <source :srcSet="project.cover" type="image/jpeg" />
        <b-carousel-slide :img-src="project.cover">
          <div :class="`text-${project.align} project-content`">
            <h1 style="line-height: 1">{{ project.title }}</h1>
            <h5 style="margin-top: -10px">{{ project.description }}</h5>
          </div>
          <b-button
            variant="outline-light"
            style="margin-bottom: 110px"
            :href="`/projects/${project.id}`"
          >
            SEE THIS PROJECTS
          </b-button>
        </b-carousel-slide>
      </picture>
    </b-carousel>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const projects = await $content('projects').fetch()
    return {
      projects,
    }
  },

  head() {
    return {
      link: [],
    }
  },
  computed: {},
}
</script>

<style lang="scss">
.kc-carousel {
  margin-top: -120px;
  width: 100%;
  height: 100vh;
}
.carousel-inner {
  height: 100vh;
}
.carousel-item {
  height: 100vh;
}
.carousel-item img {
  height: 100vh;
  object-fit: cover;
}
.carousel-indicators > li {
  border-radius: 50%;
  width: 10px;
  height: 10px;
}
.carousel-indicators {
  margin-bottom: 100px;
}
.project-content {
  margin: 0px -30px;
}
</style>
