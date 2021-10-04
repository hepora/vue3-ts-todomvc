<template>
  <li>
    <label>
      <input type="checkbox" :checked="todo.done" @change="changeState"/>
      <span>{{ todo.msg }}</span>
    </label>
    <button class="btn btn-danger" style="display:none">删除</button>
  </li>
</template>

<script>
import {defineComponent} from "vue"

export default defineComponent({
  name: "Todo",
  props: {
    todo: Object
  },
  setup(props) {
    let todo = props.todo
    let changeState = () => {
      props.todo.done = !props.todo.done
    }
    return {
      todo,
      changeState
    }
  },
})
</script>

<style scoped>

</style>