<template>
  <div class="number-container d-flex justify-content-center align-items-center">
    <!-- 减 1 的按钮 -->
    <button type="button" class="btn btn-light btn-sm" @click="reduce">-</button>
    <!-- 购买的数量 -->
    <span class="number-box">{{shopNum}}</span>
    <!-- 加 1 的按钮 -->
    <button type="button" class="btn btn-light btn-sm" @click="add">+</button>
  </div>
</template>

<script>
export default {
  data(){
    return{
      shopNum:0
    }
  },
  methods:{
      add(){
        this.shopNum++;
      },
      reduce(){
        if(this.shopNum==0) return
        this.shopNum--;
      }
  },

}
</script>

<style lang="less" scoped>
.number-box {
  min-width: 30px;
  text-align: center;
  margin: 0 5px;
  font-size: 12px;
}

.btn-sm {
  width: 30px;
}
</style>
