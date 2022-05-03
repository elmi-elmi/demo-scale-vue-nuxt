<template>
  <div>
    Event # {{ this.id }}
  </div>
</template>

<script>
export default {
  name: "_id",
  head() {
    return {
      title: `#${this.id} event  title + `,
      meta:[
        {
          hid:'description',
          name:'description',
          content:`content of event #${this.id}`
        }
      ]
    }
  },
  computed: {
    id() {
      return this.$route.params.id
    }
  }
}
</script>

<style scoped>

</style>
