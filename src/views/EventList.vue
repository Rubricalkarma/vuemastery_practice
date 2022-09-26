<template>
  <div class="events">
    <h1>Events for Good</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component'
import EventCard from '@/components/EventCard.vue'
import EventService from '@/services/EventService'

@Options({
  components: {
    EventCard,
  },
})
export default class EventList extends Vue {
  events: any = []

  created() {
    EventService.getEvents().then((response): void => {
      this.events = response.data
    })
  }
}
</script>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
