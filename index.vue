<script setup lang="ts">
import { useStore } from '@/stores'
import { localStorage } from '@/utils/local-storage'

const store = useStore()
const themeStore = localStorage.get('theme')
const checked = ref<boolean>(themeStore === 'dark')

watch(checked, (val) => {
  if (val) {
    store.mode = 'dark'
    localStorage.set('theme', 'dark')
  }
  else {
    store.mode = 'light'
    localStorage.set('theme', 'light')
  }
})
</script>

<template>
  <div class="container">
    <div class="logo" />
    <van-cell-group class="moma-cell-wrap" title="MOMA 猛玛服务" inset>
      <van-cell center title="🌗 暗黑模式">
        <template #right-icon>
          <van-switch v-model="checked" size="18px" />
        </template>
      </van-cell>
      <van-cell title="收货地址" to="address" is-link />
      <van-cell title="售后申请" to="applyAfterSales" is-link />
      <van-cell title="我的售后申请" to="mock" is-link />
    </van-cell-group>
  </div>
</template>

<style lang="less" scoped>
.container {
  width: 100vw;
  height: 100vh;
  padding-top: 30px;
  position: relative;

  .logo {
    width: 150px;
    height: 150px;
    background-image: url('@/assets/logo.png');
    background-repeat: no-repeat;
    background-size: 100% 100%;
    background-position: center;
    margin: 0 auto;
  }

  .custom-title {
    margin-right: 4px;
    vertical-align: middle;
    margin: 0 auto;
  }

  /deep/ .van-cell-group__title{
    text-align: center;
  }
}
</style>
