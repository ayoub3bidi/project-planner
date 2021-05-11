<template>
  <div class="home">
    <div v-if="projects.length">
      <div v-for="project in projects" :key="project.id">
        <SingleProject :project="project" @delete="handleDelete" @done="handleComplete" />
      </div>
    </div>
  </div>
</template>

<script>
import SingleProject from '../components/SingleProject'

export default {
  name: 'Home',
  components: { SingleProject },
  data() {
    return {
      projects: [
        {
            "id": 1,
            "title": "create new homepage",
            "details": "lorem ipsum",
            "complete": false
        },

        {
            "id": 2,
            "title": "send email",
            "details": "lorem ipsum",
            "complete": true   
        }
      ]
    }
  },
  mounted() {
    fetch('http://localhost:3000/projects')
      .then(res => res.json())
      .then(data => this.projects = data)
      .catch(err => console.log(err.message))
  },
  methods: {
    handleDelete(id) {
      this.projects = this.projects.filter((project) => {
        return project.id !== id
      })
    },
    handleComplete(id) {
      let p = this.project.find(project => {
        return project.id == id
      })
      p.complete = !p.complete
    }
  }
}
</script>
