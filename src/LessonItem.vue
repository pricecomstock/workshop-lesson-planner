<template>
  <div class="box">
    <!-- {{lesson.time}}:{{lesson.title}} -->
    <div class="field is-grouped">
      <p class="control timeinput">
        <input @input="updateTime($event.target.value)" class="input" type="number" placeholder="minutes">
      </p>
      <p class="control is-expanded">
        <input @input="updateName($event.target.value)" class="input" type="text" placeholder="name">
      </p>
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
  width:100px;
}
</style>
