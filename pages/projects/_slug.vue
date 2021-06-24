<template lang="html">
  <div>
    <b-carousel background="#ababab" class="kc-carousel">
      <picture>
        <source :srcSet="project.cover" type="image/jpeg" />
        <b-carousel-slide :img-src="project.cover">
          <div :class="`text-${project.align} project-content`">
            <h1>{{ project.title }}</h1>
            <p>{{ project.description }}</p>
          </div>
        </b-carousel-slide>
      </picture>
    </b-carousel>
    <div class="text-center">
      <b-img
        v-for="(image, index) in gallery"
        :key="index"
        :src="image"
        height="60"
        width="60"
        class="gallery"
        @click="previewImage(index)"
      >
      </b-img>
    </div>
    <b-modal
      ref="my-modal"
      hide-footer
      hide-header
      content-class="modal-background"
      size="xl"
    >
      <b-carousel
        ref="modal-carousel"
        v-model="currentImageIndex"
        :interval="4000"
        controls
        indicators
        background="#000000"
        style="text-shadow: 1px 1px 2px #333"
      >
        <picture v-for="img in gallery" :key="img">
          <source :srcSet="img" type="image/jpeg" />
          <b-carousel-slide :img-src="img"> </b-carousel-slide>
        </picture>
      </b-carousel>
    </b-modal>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const project = await $content('projects', params.slug).fetch()
    const gallery = []
    if (project.images_count) {
      for (let i = 1; i <= project.images_count; i++) {
        gallery.push(
          `/projects/${project.id}/${String(i).padStart(2, '0')}.jpg`
        )
      }
    }
    return {
      project,
      gallery,
    }
  },
  data() {
    return {
      currentImageIndex: 0,
    }
  },
  methods: {
    previewImage(index) {
      this.currentImageIndex = index
      this.$refs['my-modal'].show()
    },
  },
}
</script>

<style lang="scss">
.kc-carousel {
  margin-top: -155px;
  width: 100%;
  height: 100vh;
}
.kc-carousel .carousel-item img {
  height: 100vh;
  object-fit: cover;
}
.kc-carousel .carousel-inner {
  height: 100vh;
}
.kc-carousel .carousel-item {
  height: 100vh;
}
.kc-carousel img {
  height: 100vh;
  object-fit: cover;
}
.project-content {
  margin: 0px -30px;
}
.gallery {
  margin: 5px 5px;
}
.modal-background {
  background-color: black !important;
}
</style>
