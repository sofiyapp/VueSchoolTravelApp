<template>
    <section>
        <h1>{{experience.name}}</h1>
        <img :src="`/images/${experience.image}`" :alt="experience.name">
        <p>{{experience.descriptition}}</p>
    </section>
</template>
<script>
import sourceDate from '@/date.json'
export default {
    props:{
        id: {type: Number, required: true,},
        experienceSlug: {type: String, required:true,}
    },
    computed:{
        destination(){
            return sourceDate.destinations.find(
                destination => destination.id === this.id
            )
        },
        experience(){
            return this.destination.experiences.find(
                experience=> experience.slug === this.experienceSlug
            )
        }
    }
}
            
</script>