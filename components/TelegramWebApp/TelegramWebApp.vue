<template>
  <view>
    <button @click="initTelegramWebApp">Initialize Telegram WebApp</button>
    <view>
		<p>tel:{{tel}}</p>
    </view>
  </view>
</template>

<script setup>
import { ref } from 'vue';

const tel = ref("false");

const initTelegramWebApp = () => {
    if (window.Telegram && window.Telegram.WebApp) {
		tel.value = true;
        const tg = window.Telegram.WebApp;
        // 获取用户信息
        const initDataUnsafe = tg.initDataUnsafe;
    } else {
        console.error('Telegram WebApp is not available');
    }
}

</script>

<style scoped>
button {
  display: block;
  margin: 20px;
  padding: 10px;
  background-color: #0088cc;
  color: white;
  border: none;
  border-radius: 5px;
}
</style>