<template>
  <div>
    <h1>Events Listing</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
    <BaseIcon />
  </div>
</template>

<script>
import EventCard from '@/components/EventCard.vue'
import EventServices from '@/services/EventServices.js'

export default {
  components: {
    EventCard
  },
  data() {
    return {
      events: []
    }
  },
  created() {
    EventServices.getEvents()
      .then(response => {
        this.events = response.data
      })
      .catch(error => {
        console.log('There was an error:' + error.response)
      })
  }
}
</script>

<style></style>
