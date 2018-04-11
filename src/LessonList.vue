<template>
    <div class="container">
        <div class="columns">
            <div class="column is-one-quarter">
                <div class="field">
                    <label class="label">Start Time</label>
                    <p class="control has-icons-left">
                        <input class="input" placeholder="HH:MM" v-model="startTime">
                        <span class="icon is-small is-left">
                        <i class="fas fa-clock"></i>
                        </span>
                    </p>
                </div>
            </div>
            <div class="column is-half box">
                <lesson-item
                    v-for="(lesson, index) in lessons"
                    :key="index"
                    v-bind.sync="lesson"
                    @delete="removeLesson(index)"></lesson-item>
                <div class="buttons is-right">
                    <button class="button is-success is-outlined" @click="addItem()">New</button>
                </div>
            </div>
            <div class="column is-one-quarter">
                <p v-for="(lesson, index) in lessonsWithTime" :key="index">
                    {{lesson.timeStamp}} - {{lesson.name}}
                </p>
            </div>
        </div>
    </div>
</template>

<script>
import moment from 'moment'
import lessonItem from './LessonItem.vue'
export default {
  name: 'lessonList',
  data () {
    return {
        lessons: [
            {
                name: '',
                time: ''
            }
        ],
        startTime: ''
    }
  },
  components: {
      lessonItem
  },
  computed: {
      lessonsWithTime() {
          let time = moment(this.startTime, moment.HTML5_FMT.TIME)
          let lessonsWithTime = this.lessons.map((lesson) => {
              lesson.timeStamp = time.format('hh:mm')
              time.add(lesson.time, 'minutes')
              return lesson;
          })
          return lessonsWithTime
      }
  },
  methods: {
      addItem() {
          this.lessons.push({
              name: '',
              time: ''
          })
      },
      removeLesson(index) {
          this.lessons.splice(index, 1); // remove 1 item at index
      }
  }
}
</script>

<style lang="scss">

</style>
