<template>
  <div class="goods-container">
    <!-- 左侧图片 -->
    <div class="thumb">
      <div class="custom-control custom-checkbox">
        <!-- 复选框 -->
        <input type="checkbox" class="custom-control-input" id="cb1" :checked="shopState"  @change="stateChange"/>
        <label class="custom-control-label" for="cb1">
          <!-- 商品的缩略图 -->
          <img :src="shopPicure" alt="图片显示失败" />
        </label>
      </div>
    </div>
    <!-- 右侧信息区域 -->
    <div class="goods-info">
      <!-- 商品标题 -->
      <h6 class="goods-title">{{shopName}}</h6>
      <div class="goods-info-bottom">
        <!-- 商品价格 -->
        <span class="goods-price">￥{{shopPrice}}</span>
        <!-- 商品的数量 -->
        <Counter :ishopNum="shopNum" :ishopId="shopId"></Counter>
      </div>
    </div>
  </div>
</template>

<script>
import Counter from "@/components/Counter/Counter"
export default {
  props:{
    shopId:{
      require:true,
  
    },
    shopName:{
      default:"商品名称"
    },
    shopPrice:{
      default:0
    },
    shopPicure:{
      default:"/img/logo.png"
    },
    shopNum:{
      default:0
    },
    shopState:{
      default:0
    }
  },
  components:{
     Counter,
  },
  data(){
    return{

    }
  },
  methods:{
    stateChange(e){
      // e指向操作的对象
      console.log(e.target.checked);
      // 向父组件传值。将ID STATE 传给父组件，修改商品选中状态
      this.$emit('state-change',{id:this.shopId,state:e.target.checked})
    }
  },
  
}
</script>

<style lang="less" scoped>
.goods-container {
  + .goods-container {
    border-top: 1px solid #efefef;
  }
  padding: 10px;
  display: flex;
  .thumb {
    display: flex;
    align-items: center;
    img {
      width: 100px;
      height: 100px;
      margin: 0 10px;
    }
  }

  .goods-info {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    flex: 1;
    .goods-title {
      font-weight: bold;
      font-size: 12px;
    }
    .goods-info-bottom {
      display: flex;
      justify-content: space-between;
      .goods-price {
        font-weight: bold;
        color: red;
        font-size: 13px;
      }
    }
  }
}
</style>
