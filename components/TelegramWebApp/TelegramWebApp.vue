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

const user = ref({});
const tel = ref("false");

const initTelegramWebApp = () => {
    if (window.Telegram && window.Telegram.WebApp) {
		tel.value = true;
        const tg = window.Telegram.WebApp;
        // 获取用户信息
        const initDataUnsafe = tg.initDataUnsafe;
        this.user = initDataUnsafe.user;

        // 设置主题颜色
        tg.setBackgroundColor("#ffffff");
        tg.setHeaderColor("blue");

        // 处理关闭事件
        tg.onEvent('backButtonClicked', () => {
          console.log('Back button clicked');
        });

        // 显示主按钮
        tg.MainButton.setText('Main Button')
          .show()
          .onClick(() => {
            console.log('Main button clicked');
            tg.sendData('Button clicked'); // 向 Telegram 发送数据
          });

        console.log('Telegram WebApp initialized');
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