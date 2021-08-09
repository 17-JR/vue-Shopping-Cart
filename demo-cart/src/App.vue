<template>
  <div class="app-container">
    <Header :stitle="htitle"></Header>
    <h1>App 根组件</h1>
    <Goods></Goods>
    <Footer></Footer>
  </div>
</template>

<script>
// 导入头部
import Header from "@/components/Header/Header"
import Footer from "@/components/Footer/Footer"
import Goods from "@/components/Goods/Goods"

export default {
  // 组件引用
  components:{
    // 
    Header,
    Footer,
    Goods
  },
  data(){
    return{
      htitle:"购物车",
    }
  }
}
</script>

<style lang="less" scoped>
.app-container {
  padding-top: 45px;
  padding-bottom: 50px;
}
</style>
