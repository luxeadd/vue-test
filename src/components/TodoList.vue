<script setup>
// 親コンポーネントから子コンポーネントに値を渡す prpos
  defineProps(['todos'])
// 子コンポーネントから親コンポーネントの値を呼び出す emit
const emit = defineEmits(['removeTodo'])
// 呼び出した親コンポーネントのremoveTodoを本コンポーネント内で使用するために関数を定義
  const removeTodo = (i) => {
    emit('removeTodo', i)
  }
</script>

<template>
  <!-- v-if 条件によって要素を表示するかどうかを切り替える todosが1つ以上あれば表示
    v-showでデフォルトをdisplay;noneにすることもできる 
    v-ifの場合は条件trueにならないとそもそも存在しない -->
  <ul v-if="todos.length > 0">
    <!-- v-for取得した配列の要素を繰り返し表示  v-bind:keyは約束事で指定しておく -->
    <li v-for="(todo, i) in todos" :key="i">
      {{ todo }} <span @click="removeTodo(i)" style="cursor: pointer">x</span>
    </li>
  </ul>
  <!-- v-else ：　v-ifの直後に配置することで条件がfalseの場合の表示を指定できる -->
  <p v-else>※Todoを追加してください</p>
</template>
