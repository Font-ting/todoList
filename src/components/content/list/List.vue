<template>
  <div class="list">
    <div class="content">
      <!-- 正在进行 -->
      <div class="finish">
        <h2>正在进行</h2>
        <span class="count">{{countFinishing}}</span>
        <ul>
          <li class="finishing-li" v-for="(item,index) in listFinishing" :key="index">
            <input class="check-box" type="checkbox" @click="handelFinishingChecked($event,index)" >
            <span class="task">{{item}}</span>
            <img class="remove" src="../../../assets/img/list/remove.png" alt="" @click="handleFinishingRemoveClick(index)">
          </li>
        </ul>
      </div>
      <!-- 已经完成 -->
      <div class="finish">
        <h2>已经完成</h2>
        <span class="count">{{countFinished}}</span>
        <ul>
          <li class="finished-li" v-for="(item,index) in listFinished" :key="index">
            <input class="check-box" type="checkbox"  :checked="check" @click="handelFinishedChecked($event,index)">
            <span class="task-finished">{{item}}</span>
            <img class="remove" src="../../../assets/img/list/remove.png" alt="" @click="handleFinishedRemoveClick(index)">
          </li>
        </ul>
      </div>
    </div>
  </div>

</template>

<script>
export default {
  name: 'List',
  data () {
    return {
      countFinishing: 0,
      countFinished: 0,
      listFinished: [],
      check: false
    }
  },
  props: {
    listFinishing: {
      type: Array,
      default () {
        return []
      }
    }
  },
  updated () {
    this.countFinishing = this.listFinishing.length
    this.countFinished = this.listFinished.length
  },
  methods: {
    handelFinishingChecked (val, index) {
      if (val.target.checked) {
        val.target.checked = false
        this.listFinished.push(this.listFinishing.splice(index, 1)[0])
        this.check = true
      }
    },
    handleFinishingRemoveClick (index) {
      this.listFinishing.splice(index, 1)
    },
    handelFinishedChecked (val, index) {
      this.listFinishing.push(this.listFinished.splice(index, 1)[0])
      val.target.checked = true
    },
    handleFinishedRemoveClick (index) {
      this.listFinished.splice(index, 1)
    }
  }
}
</script>

<style scoped>
  .list{
    width:590px;
    margin:0 auto;
    padding:0 10px;
    font-size:15px;
  }
  .finish{
    margin-top:20px;
    position:relative;
  }
  ul{
    list-style:none;
  }
  .finishing-li{
    margin-left:-40px;
    height: 32px;
    line-height: 32px;
    background: #fff;
    position: relative;
    margin-bottom: 10px;
    border-radius: 3px;
    border-left: 5px solid #629A9C;
    box-shadow: 0 1px 2px rgba(0,0,0,0.07);
    position:relative;
  }
  .finished-li{
    height: 32px;
    margin-left:-40px;
    line-height: 32px;
    background: lightgray;
    position: relative;
    margin-bottom: 10px;
    padding: 0 45px;
    border-radius: 3px;
    border-left: 5px solid #999;
    border-right:1px solid #999;
    border-bottom:1px solid #999;
    border-top:1px solid #999;
    opacity: 0.4;
  }
  h2{
    color:black;
  }
  .count{
    position:absolute;
    right:6px;
    top:2px;
    padding: 0 5px;
    height: 20px;
    border-radius: 20px;
    background: #E6E6FA;
    line-height: 22px;
    text-align: center;
    color: #666;
    font-size: 14px
  }
  .check-box{
    position: absolute;
    top: 2px;
    left: 10px;
    width: 22px;
    height: 22px;
    cursor: pointer;
  }
  .task{
    position:absolute;
    top:2px;
    left:42px;
    line-height:25px;
  }
  .remove{
    position: absolute;
    top: 2px;
    right: 5px;
    display: inline-block;
    width: 14px;
    height: 12px;
    border-radius: 14px;
    border: 6px double #FFF;
    background: #CCC;
    line-height: 14px;
    text-align: center;
    color: #FFF;
    font-weight: bold;
    font-size: 14px;
    cursor: pointer;
  }
</style>
