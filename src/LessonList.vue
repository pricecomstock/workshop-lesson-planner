<template>
  <div>
    <lesson-item v-for="(lesson, index) in lessons" :key="index" v-bind.sync="lesson"></lesson-item>
    <!-- <lesson-item v-bind.sync="lesson"></lesson-item> -->
  </div>
</template>

<script>
import lessonItem from './LessonItem.vue'
export default {
  name: 'lessonList',
  data () {
    return {
        lessons: [
            {
                name: 'test',
                time: '5'
            },
            {
                name: 'test2',
                time: '15'
            }
        ]
    }
  },
  components: {
      lessonItem
  }
}
</script>

<style lang="scss">

</style>
