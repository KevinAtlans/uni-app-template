<template>
  <view class="axios-demo">
    <view class="h1">Axios Page</view>
    <u-input type="number" v-model="phone" />
    <u-button @click="getCode">获取验证码(GET)</u-button>
  </view>
</template>
<script setup>
import { ref } from 'vue'
import { userApi } from '@/api'

const phone = ref('12345678901')

const getCode = () => {
  userApi
    .getCode(phone.value)
    .then((v) => {
      uni.showToast({
        title: `${v.num}`,
        icon: 'success'
      })
    })
    .catch((err) => {
      console.log(err)
      uni.showToast({
        title: '获取验证码失败',
        icon: 'error'
      })
    })
}
</script>

<style lang="less">
.axios-demo {
  text-align: center;
}
.h1 {
  font-size: 50rpx;
}
</style>
