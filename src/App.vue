<script setup>
import { ref, computed } from "vue";
import AppHeader from "./components/AppHeader.vue";
import TodoList from "./components/TodoList.vue";

const answer = computed(() => {
  return 6 + 1;
});

const messagePull = computed(() => {
  return '<strong>'+ myName.value +'</strong>';
});

const message = ref('Hello Vue 3!');
const messageHtml = ref('<strong>Hello Vue 3!</strong>');
const welcomeBackColor = ref('red');
const welcomeColor = ref('white');
const commonMargin = ref('50px');
const myName = ref('');

const number = ref(0);
const add = () => {
  number.value++;
};

const newTodo = ref('');
const todos = ref([]);
const addTodo = () => {
  // newTodoに入力した値を配列にtodos追加
  todos.value.push(newTodo.value);
  // newTodoに入力した値をクリア
  newTodo.value = '';
};
const removeTodo = (index) => {
  // クリックした要素を削除
  todos.value.splice(index, 1);
};

const isShow = ref(false); //初期値をfalseに設定
const toggleShow = () => {
  // クリックするたびにtrueとfalseを切り替える
  isShow.value = !isShow.value;
};


</script>

<template>
  <!-- プロップスで値を渡す -->
  <!-- <AppHeader color="red" title="タイトル1"/> -->
  <!-- slotで渡す -->
  <AppHeader color="red" title="タイトル1">Todoタイトル</AppHeader>

  <p>{{ message }}</p>
  <p v-text="message"></p>
  <!-- htmlタグを認識する（エスケープしない）v-html -->
  <!-- 変数をstyle属性に代入 v-bind;style  :styleに省略も可 -->
  <!-- v-bind HTML要素の属性を動的にバインドする -->
  <p v-html="messageHtml" v-bind:style="{ backgroundColor: welcomeBackColor, color : welcomeColor }"></p>
  <p v-html="messageHtml" :style="{ backgroundColor: welcomeBackColor, color : welcomeColor }"></p>
  <p>お名前は?
    <!-- v-model 入力とデータを双方向にバインディングします -->
    <input type="text" v-model="myName" size="30">
  </p>
  <p v-html="myName" :style="{ backgroundColor : welcomeBackColor}"></p>
  <p v-html="messagePull"></p>

  <!-- イベント定義 v-on 省略@ -->
  <div class="" :style="{marginTop:commonMargin,}">
    <input type="text" size="30" v-model="number"> <button v-on:click="add">+1</button>
    <input type="text" size="30" v-model="number"> <button @click="add">+1</button>
  </div>

  <div class="" :style="{marginTop:commonMargin}">
    <input type="text" size="30" v-model="newTodo">
    <button @click="addTodo()">追加</button>
    <!-- proosでコンポーネントにtodosを渡す、emitで親removeTodoを子removeTodoと関連づける -->
    <TodoList :todos="todos" @removeTodo="removeTodo"/>
  </div>

  <div class="" :style="{marginTop:commonMargin}">
    <button @click="toggleShow">クリック</button>
    <p v-show="isShow">表示</p>
  </div>


</template>
