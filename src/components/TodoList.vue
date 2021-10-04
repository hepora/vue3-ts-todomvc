<template>
  <ul class="todo-main">
    <Todo v-for="item in allTodo" :todo="item" :key="item.id"/>
    <!--          <li>-->
    <!--            <label>-->
    <!--              <input type="checkbox"/>-->
    <!--              <span>xxxxx</span>-->
    <!--            </label>-->
    <!--            <button class="btn btn-danger" style="display:none">删除</button>-->
    <!--          </li>-->
    <!--          <li>-->
    <!--            <label>-->
    <!--              <input type="checkbox"/>-->
    <!--              <span>yyyy</span>-->
    <!--            </label>-->
    <!--            <button class="btn btn-danger" style="display:none">删除</button>-->
    <!--          </li>-->
  </ul>
</template>

<script>
import {defineComponent, onMounted, onUpdated} from "vue"
import Todo from "@/components/Todo";

export default defineComponent({
  name: "TodoList",
  components: {Todo},
  props: {
    data: Object
  },
  setup(props) {
    let allTodo = props.data
    onMounted(() => {
      console.log("mounted收到的alltodo", allTodo)
    })
    onUpdated(() => {
      console.log("update接收到的alltodo", allTodo)
    })
    return {
      allTodo
    }
  }
})
</script>

<style scoped>

</style>