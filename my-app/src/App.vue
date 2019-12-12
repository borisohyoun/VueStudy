<template>
  <div id="app">
   <TodoHeader></TodoHeader>
   <TodoInput v-on:addTodo="addTodo"></TodoInput>
   <TodoList v-bind:propsdata="todoItems" v-on:removeTodo="removeTodo"></TodoList>
   <!-- TodoFooter에서 발생시킬 이벤트의 이름은 removeAll, 상위 컴포넌트인 App.vue에서 받아와서 실행시킬 메서드 이름이 clearAll -->
   <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  components:{
    'TodoHeader':TodoHeader,
    'TodoInput':TodoInput,
    'TodoList':TodoList,
    'TodoFooter':TodoFooter
  },
  data(){
    //데이터 속성 todoItems선언
    return{
      todoItems:[]
    }
  },
  methods:{
    addTodo(todoItem){
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    clearAll(){
      localStorage.clear();
      this.todoItems = [];
    },
    removeTodo(todoItem,index){
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index,1);
    }
  },
  created(){
        if(localStorage.length > 0){
            for(var i = 0; i < localStorage.length; i++){
                this.todoItems.push(localStorage.key(i));
            }
        }
    },
}
</script>

<style>
  body{
        text-align: center;
        background-color: #F6F6F8;
    }
  input{
    border-style:groove;
    width:200px;
  }
  button{
    border-style: groove;
  }
  .shadow{
    box-shadow: 5px 10px 10px rgba(0,0,0,0.03);
  }
</style>
