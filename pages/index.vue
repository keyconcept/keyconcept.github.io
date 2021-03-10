<template lang="html">
  <div class="">
    <b-carousel
      :interval="4000"
      controls
      indicators
      background="#ababab"
      class="kc-carousel"
    >
      <picture v-for="(img, index) in landingGalleryJPG" :key="img">
        <source :srcSet="landingGalleryWEBP[index]" type="image/webp" />
        <source :srcSet="img" type="image/jpeg" />
        <b-carousel-slide :img-src="img"> </b-carousel-slide>
      </picture>
    </b-carousel>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentImageIndex: 0,
      landingGalleryJPG: [
        require('~/assets/images/landing-3-01.jpg'),
        require('~/assets/images/landing-3-02.jpg'),
        require('~/assets/images/landing-3-03.jpg'),
        require('~/assets/images/landing-3-04.jpg'),
        require('~/assets/images/landing-3-05.jpg'),
        require('~/assets/images/landing-3-06.jpg'),
        require('~/assets/images/landing-3-08.jpg'),
        require('~/assets/images/landing-3-09.jpg'),
        require('~/assets/images/landing-3-10.jpg'),
        require('~/assets/images/landing-3-11.jpg'),
        require('~/assets/images/landing-3-12.jpg'),
        require('~/assets/images/landing-3-13.jpg'),
        require('~/assets/images/landing-3-14.jpg'),
        require('~/assets/images/landing-3-15.jpg'),
        require('~/assets/images/landing-3-16.jpg'),
      ],
      landingGalleryWEBP: [
        require('~/assets/images/landing-3-01.jpg?webp'),
        require('~/assets/images/landing-3-02.jpg?webp'),
        require('~/assets/images/landing-3-03.jpg?webp'),
        require('~/assets/images/landing-3-04.jpg?webp'),
        require('~/assets/images/landing-3-05.jpg?webp'),
        require('~/assets/images/landing-3-06.jpg?webp'),
        require('~/assets/images/landing-3-08.jpg?webp'),
        require('~/assets/images/landing-3-09.jpg?webp'),
        require('~/assets/images/landing-3-10.jpg?webp'),
        require('~/assets/images/landing-3-11.jpg?webp'),
        require('~/assets/images/landing-3-12.jpg?webp'),
        require('~/assets/images/landing-3-13.jpg?webp'),
        require('~/assets/images/landing-3-14.jpg?webp'),
        require('~/assets/images/landing-3-15.jpg?webp'),
        require('~/assets/images/landing-3-16.jpg?webp'),
      ],
    }
  },
  head() {
    return {
      link: [],
    }
  },
  computed: {},
  methods: {
    previewImage(index) {
      this.currentImageIndex = index
      this.$refs['my-modal'].show()
    },
  },
}
</script>

<style lang="css">
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
</style>
