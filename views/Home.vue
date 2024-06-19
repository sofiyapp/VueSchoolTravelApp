<template>
  <div class="home">
    <h1>All Destinations</h1>
    <button @click="triggerRouterError">Trigger Router Error</button>
    <div class="destinations">
      <router-link
        v-for="destination in destinations"
        :key="destination.id"
        :to="{ name: 'destination.show', params: { id: destination.id, slug: destination.slug } }"
      >
        <div>
          <h2>{{ destination.name }}</h2>
          <img :src="`/images/${destination.image}`" :alt="destination.name" />
        </div>
      </router-link>
    </div>
  </div>
</template>

<script>
import sourceData from '@/data.json'
import { isNavigationFailure, NavigationFailureType } from "vue-router"

export default {
  data() {
    return {
      destinations: sourceData.destinations
    }
  },
  methods: {
    async triggerRouterError() {
      try {
        // Attempt to navigate to the current route
        await this.$router.push('/')
      } catch (error) {
        // Handle navigation errors
        if (isNavigationFailure(error, NavigationFailureType.duplicated)) {
          console.log('Duplicate navigation detected:')
          console.log('To:', error.to)
          console.log('From:', error.from)
        } else {
          console.error('Navigation error:', error)
        }
      }
    }
  }
}
</script>
