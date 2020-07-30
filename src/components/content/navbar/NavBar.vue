<template>
  <div class="nav-bar">
    <div class="content">
      <span>ToDoList</span>
      <input v-model="taskText" type="text" placeholder="添加任务" @keyup.enter="handelKeyupEnter($event)">
    </div>
  </div>

</template>

<script>
export default {
  name: 'NavBar',
  data () {
    return {
      taskText: ''
    }
  },
  methods: {
    handelKeyupEnter (event) {
      this.$emit('handleKeyup', event.target.value)
      event.target.value = ''
    }
  }
}
</script>

<style scoped>
.nav-bar{
  height:50px;
  background-color: rgba(47,47,47,0.98);
}
.content{
  width:600px;
  padding:0px 10px;
  margin:0 auto;
}
span{
  font-size:24px;
  line-height: 50px;
  margin-right:125px;
  color:#DDD;
}
input{
  /* 字体首行缩进 */
  text-indent:10px;
  width:60%;
  height:24px;
  border-radius: 5px;
  font-size:14px;
  box-shadow: 0 1px 0 rgba(255,255,255,0.24), 0 1px 6px rgba(0,0,0,0.45) inset;
}

</style>
