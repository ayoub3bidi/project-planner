<template>
  <div class="project">
      <div class="actions">
          <h3 @click="showDetails = !showDetails">{{ project.title }}</h3>
          <div class="icons">
              <i class="far fa-edit"></i>
              <i class="far fa-trash-alt"></i>
              <i class="far fa-check-circle"></i>
          </div>
      </div>
      <div v-if="showDetails" class="details">
          <p>{{ project.details }}</p>
      </div>
  </div>
</template>

<script>
export default {
    props : ['project'],
    data() {
        return {
            showDetails: false
        }
    }

}
</script>

<style>
    .project {
        margin: 20px auto;
        background: white;
        padding: 10px 20px;
        border-radius: 4px;
        box-shadow: 1px 2px 3px rgba(0,0,0,0.5);
        border-left: 4px solid #e90074;
    }
    h3 {
        cursor: pointer;
    }
    .actions {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .far {
        font-size: 24px;
        margin-left: 10px;
        color: #bbb;
        cursor: pointer;
    }
    .far:hover {
        color: #777;
    }
</style>