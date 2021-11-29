<script lang="ts">
import { defineComponent } from '#app'
import { mdiMapMarker, mdiCircleMedium } from '@mdi/js'

export default defineComponent({
  name: 'FJobCard',

  props: {
    title: String,
    department: String,
    location: String,
    isRemote: Boolean,
    description: String,
    link: String,
  },

  setup() {
    return {
      mdiMapMarker,
      mdiCircleMedium,
    }
  },
})
</script>

<template>
  <v-card class="f-job-card" elevation="0">
    <v-card-subtitle
      class="f-job-card__subtitle pb-2 primary--text font-weight-bold"
      v-text="department"
    />

    <v-card-title class="f-job-card__title pt-0 pb-2" v-text="title" />

    <v-card-text>
      <v-layout justify-space-between class="text-caption mb-6">
        <v-layout align-center>
          <v-icon
            class="f-job-card__location-icon mr-1"
            size="16"
            color="primary"
            >{{ mdiMapMarker }}</v-icon
          >

          <p
            class="f-job-card__location-title font-weight-bold mb-0"
            v-text="location"
          />
        </v-layout>

        <p class="f-job-card__location-remote primary--text mb-0">Remote</p>
      </v-layout>

      <p
        class="f-job-card__description mb-4"
        v-snip="4"
        v-html="description"
      ></p>

      <a
        :href="link"
        rel="nofollow noopener"
        target="_blank"
        class="f-job-card__link mb-2"
      >
        <v-layout align-center class="text-body-2 font-weight-bold">
          <v-icon color="primary" class="mr-1" small>{{
            mdiCircleMedium
          }}</v-icon>
          <span class="f-job-card__link-text text-decoration-underline"
            >Learn More</span
          >
        </v-layout>
        <div>
          <small>{{ link }}</small>
        </div>
      </a>
    </v-card-text>
  </v-card>
</template>

<style lang="scss" scoped>
.f-job-card {
  border: 2px solid var(--v-off-white-base) !important;

  &__subtitle {
    font-size: 12px;
  }

  &__link-text {
    color: #3c4146;
  }
  &:hover {
    .f-job-card__link-text {
      color: var(--v-primary-base);
    }
  }
}
</style>
