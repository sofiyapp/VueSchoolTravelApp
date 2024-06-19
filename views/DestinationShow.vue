<template>
    <div>
      <section v-if="destination" class="destination">
        <h1>{{ destination.name }}</h1>
        <GoBack />
        <div class="destination-details">
          <img :src="`/images/${destination.image}`" :alt="destination.name">
          <p>{{ destination.description }}</p>
        </div>
      </section>
      <section class="experiences">
        <h2>Top Experiences in {{ destination.name }}</h2>
        <div class="cards">
          <router-link v-for="experience in destination.experiences"
                       :key="experience.slug"
                       :to="{ name: 'experience.show', params: { id: destination.id, experienceSlug: experience.slug }}">
            <ExperienceCard :experience="experience" />
          </router-link>
        </div>
        <router-view />
      </section>
    </div>
  </template>
  
  <script setup>
  import sourceData from '@/data.json'
  import GoBack from '@/components/GoBack.vue'
  import ExperienceCard from '@/components/ExperienceCard.vue'
  
  const props = defineProps(['id'])
  
  const destination = computed(() => {
    return sourceData.destinations.find(dest => dest.id === id)
  })
  </script>
  