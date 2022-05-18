<template>
  <div>
    <h1>Event</h1>
    <EventCard
      v-for="(event,idx) in events"
      :key="idx"
      :event="event"
      :data-index="idx"
    />
  </div>
</template>

<script>
import EventCard from "@/components/EventCard";
import {mapState} from 'vuex';
export default {
  head() {
    return {
      title: 'Title from index.vue',
    }
  },
  components: {EventCard},
  name: 'IndexPage',
  computed:mapState({
    events:state=>state.events.events
  }),
  async asyncData({store, error}) {
    try{
    await store.dispatch('events/fetchEvents')
    }catch(e){
        error({
          statusCode:503,
          message:'Unabel to fetch events at this time. Please try again.'
        })
    }

  }

}
</script>
