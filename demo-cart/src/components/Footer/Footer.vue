<template>
  <div class="footer-container">
    <!-- 左侧的全选 -->
    <div class="custom-control custom-checkbox">
      <input type="checkbox" class="custom-control-input" id="cbFull" :checked="true" />
      <label class="custom-control-label" for="cbFull">全选</label>
    </div>

    <!-- 中间的合计 -->
    <div>
      <span>合计：</span>
      <span class="total-price">￥{{ 0 }}</span>
    </div>

    <!-- 结算按钮 -->
    <button type="button" class="btn btn-primary btn-settle">结算（{{ 0 }}）</button>
  </div>
</template>

<script>
export default {}
</script>

<style lang="less" scoped>
// 底部边框
.footer-container {
  // 字体大小
  font-size: 12px;
  // 宽高
  height: 50px;
  width: 100%;
  border-top: 1px solid #efefef;
  // 固定定位
  position: fixed;
  // 固定在底部
  bottom: 0;
  // 背景颜色
  background-color: #fff;
  // 弹性布局
  display: flex;
  // 水平均匀分布
  justify-content: space-between;
  // 字体居中
  align-items: center;
  // 左右边距
  padding: 0 10px;
}
// 全选按钮
.custom-checkbox {
  // 弹性布局，垂直居中
  display: flex;
  align-items: center;
}
// 
#cbFull {
  margin-right: 5px;
}

.btn-settle {
  height: 80%;
  // 定义最小宽度
  min-width: 110px;
  border-radius: 25px;
  font-size: 12px;
}

.total-price {
// 字体加粗
  font-weight: bold;
// 字体大小
  font-size: 14px;
  color: red;
}
</style>
