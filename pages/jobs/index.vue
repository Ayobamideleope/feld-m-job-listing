<script lang="ts">
import { defineComponent } from '#app'
import FHeroSection from '~/components/sections/FHeroSection.vue'
import FJobs from '~/components/pages/jobs/FJobs.vue'
import { NuxtAxiosInstance } from '@nuxtjs/axios'

export default defineComponent({
  name: 'JobsPage',

  head: {
    title: 'Open Jobs',
  },

  components: {
    FHeroSection,
    FJobs,
  },

  async asyncData({ $axios }: { $axios: NuxtAxiosInstance }) {
    let offers = []

    try {
      const data = await $axios.$get('https://feldm.recruitee.com/api/offers')

      offers = data.offers
    } catch (error) {
      console.error(error)
    }

    return { offers }
  },
})
</script>

<template>
  <div>
    <f-hero-section
      title="Open Jobs"
      imgSrc="/img/backgrounds/pexels-fauxels-3184423.jpg"
      class="mb-6 mb-8"
    />

    <v-container class="max-width-800">
      <p class="mb-10">
        Would like to work with us? Below are some of our current open roles...
      </p>
    </v-container>

    <f-jobs :offers="offers" />
  </div>
</template>
