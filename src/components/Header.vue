<template>
  <div class="todo-header">
    <input
        type="text"
        placeholder="请输入你的任务名称，按回车键确认"
        v-model="msg"
        @keyup.enter="addOne"
    />
  </div>
</template>

<script>
import {defineComponent, ref} from "vue"

export default defineComponent({
  name: "Header",
  setup(props, context) {
    let msg = ref("")
    let addOne = () => {
      context.emit("addOne", msg.value.trim())
      msg.value = ""
    }
    return {
      msg,
      addOne
    }
  }
})
</script>

<style scoped>

</style>