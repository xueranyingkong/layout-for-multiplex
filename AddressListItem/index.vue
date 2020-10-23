<template>
  <div class="container">
    <!-- <div class="address-list-item"> -->
    <div class="left-msg">
      <div class="left-msg-select">
        <img src="@/static/willBill/selected.png">
        <span></span>
      </div>
      <div class="left-msg-main">
        <span class="left-msg-main-address">山东省青岛市李沧区九水东路青岛国际创新园A座32-5-6 际创新园A座32-5-6</span>
        <div class="left-msg-main-user">
          <span class="left-msg-main-user-default">默认</span>
          <span class="left-msg-main-user-name">李一帆</span>
          <span class="left-msg-main-user-phone">13275325689</span>
        </div>
      </div>
    </div>
    <div class="right-btn">
      <i class="el-icon-edit"></i>
    </div>
    <!-- </div> -->
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.container {
  padding: 20px;
  // height: 100px;
  background: #f8f8f8;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  .left-msg {
    display: flex;
    align-items: center;
    &-select {
      padding-right: 20px;
      img {
        height: 20px;
        width: 20px;
      }
    }
    &-main {
      width: 80%;
      &-address {
        font-size: 16px;
        color: #333;
        line-height: 17px;
      }
      &-user {
        padding-top: 15px;
        &-default {
          color: #051878;
          font-size: 14px;
          padding: 5px 10px;
          background: #0518781a;
          border-radius: 6px;
          margin-right: 14px;
        }
        &-name,
        &-phone {
          font-size: 14px;
          color: #999;
          margin-right: 14px;
        }
      }
    }
  }
  .right-btn {
    height: 20px;
    width: 20px;
  }
}
</style>