<script lang="ts">
import { defineComponent } from '#app'

export default defineComponent({
  name: 'FHeroSection',

  props: {
    title: {
      type: String,
      required: true,
    },
    imgSrc: {
      type: String,
      required: true,
    },
  },

  setup() {
    return {}
  },
})
</script>

<template>
  <section
    class="
      f-hero-section
      position-relative
      d-flex
      align-center
      justify-center
      overflow-x-hidden
    "
  >
    <v-img
      :src="imgSrc"
      class="f-hero-section__img position-absolute w-100 h-100"
    />

    <h1
      class="
        text-h4 text-sm-h3
        position-relative
        white--text
        font-weight-bold
        text-center
      "
    >
      {{ title }}
    </h1>
  </section>
</template>

<style lang="scss" scoped>
.f-hero-section {
  height: 240px;
  padding: 100px 24px;

  &::before {
    content: '';
    position: absolute;
    top: 24px;
    left: 12px;
    width: 100%;
    height: 100%;
    background-color: #d4dcd7;

    @media #{map-get($display-breakpoints, 'sm-and-up')} {
      left: 24px;
    }
  }

  &__img::after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
  }

  @media #{map-get($display-breakpoints, 'sm-and-up')} {
    padding: 200px 24px;
    height: 400px;
  }
}
</style>
