<template lang="html">
  <div class="">
    <b-carousel
      :interval="6000"
      controls
      indicators
      background="#ababab"
      class="kc-carousel"
    >
      <picture v-for="project in projects" :key="project.id">
        <source :srcSet="project.cover" type="image/jpeg" />
        <b-carousel-slide :img-src="project.cover">
          <b-row>
            <div
              :class="`text-${project.align} project-content`"
              :style="`${project.align}`"
            >
              <h1 style="line-height: 1">
                {{ project.title }}
                {{ project.project_year ? `(${project.project_year})` : '' }}
              </h1>
              <h5 style="margin-top: -10px">{{ project.description }}</h5>
              <table
                :class="`text-${project.align} info-table`"
                :style="{ float: project.align }"
              >
                <tr>
                  <td class="table-title">Location :</td>
                  <td class="table-value">{{ project.location }}</td>
                </tr>
                <tr>
                  <td class="table-title">Owner :</td>
                  <td class="table-value">{{ project.owner }}</td>
                </tr>
                <tr>
                  <td class="table-title">Area :</td>
                  <td class="table-value">{{ project.area }}</td>
                </tr>
                <tr>
                  <td class="table-title">Budget :</td>
                  <td class="table-value">{{ project.budget }}</td>
                </tr>
                <tr>
                  <td class="table-title">Designed by :</td>
                  <td class="table-value">{{ project.designed_by }}</td>
                </tr>
                <tr>
                  <td class="table-title">Style :</td>
                  <td class="table-value">{{ project.style }}</td>
                </tr>
              </table>
            </div>
          </b-row>
          <b-button
            variant="outline-light"
            style="margin: 20px 20px 110px 20px"
            :href="`/projects/${project.id}`"
          >
            See more images
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
.info-table {
  line-height: 18px;
  font-size: 18px;
  .table-title {
    text-align: right;
    text-transform: uppercase;
    padding-right: 10px;
  }
}
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
