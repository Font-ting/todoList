<template>
  <div id="app">
    <nav-bar ref="navbar" @handleKeyup="handleListData"></nav-bar>
    <list :listFinishing="todoList"></list>
    <router-view/>
  </div>
</template>

<script>
import NavBar from '@/components/content/navbar/NavBar'
import List from '@/components/content/list/List'
export default {
  name: 'App',
  data(){
    return{
      todoList:[]
    }
  },
  components:{
    NavBar,
    List
  },
  methods:{
    handleListData(val){
      this.todoList.push(val);
    }
  },
  mounted(){
    
  }
}
</script>
<style>
body{
  margin:0;
  padding:0;
  background-color:#cdcdcd;
}
</style>
