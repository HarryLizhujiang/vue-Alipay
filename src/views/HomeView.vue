<template>
	<div class="home">
		<img alt="Vue logo" src="../assets/logo.png" />
		<div class="btn" @click="goplayment">点击购买</div>
	</div>
</template>

<script>
import axios from 'axios';
import qs from 'qs';
export default {
	name: 'HomeView',
	components: {},
	methods: {
		goplayment() {
			// 参数
			let data = {
				orderId: 'aa123456789112233', //订单编号 一般由后端生成
			};

			// 向后端请求支付
			axios({
				url: '/api/playment',
				method: 'post',
				headers: { 'content-type': 'application/x-www-form-urlencoded' },
				data: qs.stringify(data),
			}).then((res) => {
				console.log(res);
				// 拿到后端返回的支付宝地址进行跳转
				window.location.href = res.data.result;
			});
		},
	},
};
</script>
<style lang="scss">
.btn {
	width: 100px;
	heigth: 100px;
	border: solid 1px black;
	margin: 0 auto;
}
</style>
