<template>
	<view>
		<button class="connect-button" @click="connectToWallet">Connect Wallet</button>
		<text>{{connectedW}}</text>
	</view>
</template>

<script setup>
	import {ref} from 'vue';
	import {onLoad} from "@dcloudio/uni-app"
	import { TonConnect } from '@tonconnect/sdk';
	
	const connectedW = ref("");

	const tonConnectUI = new TON_CONNECT_UI.TonConnectUI({
	    manifestUrl: 'https://minayun456.github.io/my-twa/tonconnect-manifest.json'
	});
	
	async function connectToWallet() {
	    const connectedWallet = await tonConnectUI.connectWallet();
	    // 如果需要，可以对connectedWallet做一些事情
		connectedW.value = connectedWallet;
	    console.log(connectedWallet);
	}

</script>

<style lang="scss" scoped>
	.connect-button{
		background-color: blue;
	}
</style>