<template>
  <div id="root">
    <div class="todo-container">
      <div class="todo-wrap">
        <Header @addOne="addOne"/>
        <TodoList :data="data"/>
        <Footer :todo="data" @cleanDone="cleanAllDone"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import {defineComponent, onMounted, reactive, ref} from "vue"
import "../public/todos_page/index.css"
import TodoList from "@/components/TodoList.vue";
import Footer from "@/components/Footer.vue";
import Header from "@/components/Header.vue";

export default defineComponent({
  name: "App",
  components: {
    Header,
    Footer,
    TodoList
  },
  setup() {
    /*定义数据*/
    let data = reactive([
      {id: 1, msg: "你好啊", done: false},
      {id: 2, msg: "不好啊", done: true},
      {id: 3, msg: "好啊", done: false},
      {id: 4, msg: "好啊", done: true},
      {id: 5, msg: "好啊", done: true},
    ])
    /*定义方法*/
    let cleanAllDone = () => {
      console.log("开始清除")
      cleanDone(data)
      console.log('清除完毕')
    }
    let cleanDone = (todo: any) => {
      todo.forEach((item: any, index: number) => {
        if (item.done) {
          todo.splice(index, 1)
          return cleanDone(todo)
        }
      })
    }
    /*添加一条数据*/
    let addOne = (msg: string) => {
      // console.log(msg)
      let id: number
      if (data.length > 0) {
        id = data[data.length - 1].id + 1
      } else {
        id = 1
      }
      data.push({id, msg, done: false})
    }
    return {
      data,
      cleanAllDone,
      addOne
    }
  }
})
</script>

<style>
</style>
