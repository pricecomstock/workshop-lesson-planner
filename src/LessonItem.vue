<template>
  <div class="level">
    <!-- {{lesson.time}}:{{lesson.title}} -->
    <div class="level-left">
      <div class="level-item">
        Up/Down
      </div>
    </div>
    <div class="level-item">
      <div class="field is-grouped">
        <p class="control timeinput has-icons-left">
          <input @input="updateTime($event.target.value)" class="input" type="number" placeholder="minutes">
          <span class="icon is-small is-left">
            <i class="fas fa-clock"></i>
          </span>
        </p>
        <p class="control is-expanded has-icons-left">
          <input @input="updateName($event.target.value)" class="input" type="text" placeholder="name">
          <span class="icon is-small is-left">
            <i class="fas fa-lightbulb"></i>
          </span>
        </p>
      </div>
    </div>
    <div class="level-right">
      <div class="level-item">
        <button class="delete" @click="$emit('delete')"></button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'lessonItem',
  data () {
    return {
    }
  },
  props: {
      name: {
          type: String,
          required: false
      },
      time: {
          type: String,
          required: false
      }
  },
  methods: {
    updateTime(newTime) {
      this.$emit('update:time', newTime)
    },
    updateName(newName) {
      this.$emit('update:name', newName)
    }
  }
}
</script>

<style lang="scss">
.timeinput {
  width:130px;
}
</style>
