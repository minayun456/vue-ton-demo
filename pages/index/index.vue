<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<TelegramWebApp />
		<button class="button" @click="openBrowser">付款</button>  
	</view>
</template>

<script setup>
	const openBrowser = ()=>{  
	    plus.runtime.openURL('https://app.tonkeeper.com/transfer/'
			+'0QAKiDdiRH0AQqcdDbrJA0_Adxboy8i4dur_T-fMYYp-oN6C'
			+'?amount=1000000000&text=abcc');
	    }
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
