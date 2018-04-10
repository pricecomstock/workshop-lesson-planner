<template>
  <div id="app">
    <div class="section">
      <div class="container">
        <div class="columns is-centered">
          <lesson-list class="column is-half"></lesson-list>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import lessonList from './LessonList.vue'
export default {
  name: 'app',
  data () {
    return {
    }
  },
  components: {
    lessonList
  }
}
</script>

<style lang="scss">
</style>
