<template>
  <div class="app-container">
    <Header :stitle="htitle"></Header>
    <Goods v-for="item in shoplist" 
    :key="item.id" :shopName="item.goods_name" 
    :shopPrice="item.goods_price" :shopPicure="item.goods_img"
    :shopId="item.id"
    :shopNum="item.goods_count"
    :shopState="item.goods_state"
    @state-change="getNewState"
    ></Goods>
    <Footer :fullstate="fullstate" :fullprice="fullprice" @change-fullstate="isfull" :sumNum="sumShopNum"></Footer>
  </div>
</template>

<script>
// 导入axios
import axios from "axios"
// 导入组件
import Header from "@/components/Header/Header"
import Footer from "@/components/Footer/Footer"
import Goods from "@/components/Goods/Goods"

import bus from "@/components/eventBus"

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
      shoplist:[]
    }
  },
  created(){
    // 调用数据获取 
    this.inertCartList();
    bus.$on('shopNum-change',val=>{
      this.shoplist.some(item=>{
        if(item.id===val.id){
          item.goods_count=val.shopNum;
        }
      })
    })
  },
  methods:{
    // 封装商品数据获取方式
    async inertCartList(){
     const {data:res}= await axios.get('https://www.escook.cn/api/cart');
     console.log(res)
        if(res.status===200){
          this.shoplist=res.list;
        }
        else{
          alert("商品信息获取失败，请刷新")
        }
    },
    // 响应子组件传过来的值，修改商品状态
    getNewState(val){
      console.log(val);
      // 循环遍历，通过ID 查找商品
      this.shoplist.some(item=>{
        if(item.id===val.id){
          item.goods_state=val.state;
          return true;
        }
      })
    },
    //接收全选状态变化
    isfull(val){
      this.shoplist.forEach(item => {
        item.goods_state=val;
      });
    }
  },
  // 计算属性
  computed:{
    // 是否全选
    fullstate(){
      return this.shoplist.every(item=>item.goods_state===true);
    },
    //计算商品总价
    fullprice(){
        return this.shoplist
        // 先使用filter过滤
        .filter(item=>item.goods_state)
        // 再使用reduce 累加
        .reduce((tatol,item)=>{
          return tatol +=item.goods_count * item.goods_price;
      },0)
    },
    // 计算选中商品总数
    sumShopNum(){
      return this.shoplist.filter(item=>item.goods_state).reduce((sum,item)=>{
       return  sum +=item.goods_count;
      },0)
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
