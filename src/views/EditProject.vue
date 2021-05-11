<template>
  <h1>Edit project</h1>
  <form>
      <label for="">Title:</label>
      <input type="text" v-model="title" required>
      <label for="">Details:</label>
      <textarea v-model="details" required></textarea>
      <button>Update Project</button>
  </form>
</template>

<script>
export default {
  props: ['id'],
  data() {
    return {
      title: '',
      details: '',
      uri: 'http://localhost:3000/projects/' + this.id
    }
  },
  mounted() {
    fetch(this.uri)
      .then(res => res.json())
      .then(data => {
        this.title = data.title
        this.details = data.details
      })
  }
}
</script>

<style>

</style>