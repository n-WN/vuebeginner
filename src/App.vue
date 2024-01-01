<script setup>
import { ref } from 'vue'

// 给每个 todo 对象一个唯一的 id
let id = 0

const newTodo = ref('')
const todos = ref([
  { id: id++, text: 'Learn HTML' },
  { id: id++, text: 'Learn JavaScript' },
  { id: id++, text: 'Learn Vue' }
])

function addTodo() {
  // console.log(newTodo.value.trim())
  if (!(newTodo.value === '')) { // 同时比较类型
    const newTask = {
      id: id++, text: newTodo.value
    }
    todos.value.push(newTask)
    newTodo.value = '' // 清空输入框
  }
}

function removeTodo(todo) {
  // console.log(todo)
  // 做法 1
  // const index = todos.value.indexOf(todo); // 找到要删除的元素在数组中的索引位置
  // if (index !== -1) { // 比较两个值是否不相等且类型也不相等
  //   todos.value.splice(index, 1)
  // }

  // 做法 2
  // 使用 filter 方法过滤掉需要删除的元素，只返回那些 id 不等于被点击的 todo 的元素。最后，重新赋值给 todos
  // todos.value = todos.value.filter(item => item.id !== todo.id)
  todos.value = todos.value.filter(item => item !== todo) // 解释在下面
}
</script>

<template>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo">
    <button>Add Todo</button>
  </form>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      {{ todo }}
<!--      {{ todo.id }}-->
<!--      {{ todo.text }}-->
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
</template>