<template>
  <h1>
     {{ this.event.title }}
  </h1>
</template>

<script>
import EventService from "@/services/EventService";

export default {
  name: "EventUser",
  head() {
    return {
      title: this.event.title,
      meta:[
        {
          hid:'description',
          name:'description',
          content:`content of event #${this.event.id}`
        }
      ]
    }
  },
  computed: {
    id() {
      return this.$route.params.id
    }
  },
  async asyncData({ error, params}) {
    try{

      const {data}= await EventService.getEvent(params.id)
      return {
        event: data
      }
    }catch(e){
      error({
        statusCode:503,
        message:'Unabel to fetch event #'+params.id
      })
    }

  }
}
</script>

<style scoped>

</style>
