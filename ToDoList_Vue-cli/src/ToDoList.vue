<template>
  <div>
    <div>
      <input v-model="inputValue"/>
      <button @click="submit">提交</button>
    </div>
    <div>
      <ul>
        <todo-item
                v-for="(item,index) of list"
                :key="index"
                :content="item"
                :index="index"
                @delete="handleDelete"

        ></todo-item>
      </ul>
    </div>
  </div>
</template>

<script>
import ToDoItem from './components/ToDoItem.vue'
import TodoItem from "./components/ToDoItem";
export default {
    components:{
        TodoItem,
        'todo-item':ToDoItem
    },
  data:function(){
      return{
          inputValue:'',
          list:[]
      }
  },
    methods:{
      submit:function(){
          this.list.push(this.inputValue)
          this.inputValue=''
      },
        handleDelete(index){
          var con = confirm("确定要删除该条记录吗?")
            if(con){
              this.list.splice(index,1)
            }
        }
    }
}
</script>

<style>

</style>
