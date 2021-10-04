<template>
  <div class="todo-footer">
    <label>
      <input type="checkbox" :checked="leftLength===0" @change="changeAllState"/>
    </label>
    <span>
          <span>已完成{{ num - leftLength }}</span> / 全部{{ num }}
        </span>
    <button class="btn btn-danger" @click="cleanAllDone">清除已完成任务</button>
  </div>
</template>

<script>
import {computed, defineComponent} from "vue"

export default defineComponent({
  name: "Footer",
  props: {
    todo: Object
  },
  setup(props, context) {
    let leftLength = computed(() => {
      if (num.value === 0) {
        return false
      }
      return props.todo.filter(item => {
        return !item.done
      }).length
    })
    let num = computed(() => {
      return props.todo.length
    })
    let cleanAllDone = () => {
      context.emit("cleanDone")
    }
    let changeAllState = () => {
      if (leftLength.value === 0) {
        props.todo.forEach(item => {
          item.done = false
        })
      } else {
        props.todo.forEach(item => {
          item.done = true
        })
      }

    }
    return {
      cleanAllDone,
      changeAllState,
      leftLength,
      num
    }
  }
})
</script>

<style scoped>

</style>