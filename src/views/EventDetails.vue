<template lang="pug">
div(v-if='event')
  h1 {{ event.title }}
  p {{ event.time }} on {{ event.date }} @ {{ event.location }}
  p {{ event.description }}
</template>

<script>
import EventService from '@/services/EventService.js'

export default {
  props: ['id'],
  data() {
    return {
      event: null,
    }
  },
  created() {
    EventService.getEvent(this.id)
      .then((response) => (this.event = response.data))
      .catch((error) => console.log(error))
  },
}
</script>
