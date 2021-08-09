<template>
  <div class="header-container">{{title}}</div>
</template>

<script>
export default {
  // 自定义属性，传值
  props:{
    stitle:{
      default:"标题"
    }
  },
  data(){
    return{
       title:this.stitle,
    }
   
  }
}
</script>

<style lang="less" scoped>
.header-container {
  font-size: 12px;
  height: 45px;
  width: 100%;
  background-color: #1d7bff;
  // 弹性布局
  display: flex;
  justify-content: center;
  align-items: center;
  color: #fff;
  // 固定定位
  position: fixed;
  top: 0;
  z-index: 999;
}
</style>
