<template>
	<div class="about">
		<h1>支付结果页</h1>
	</div>
</template>
<script>
import axios from 'axios';
import qs from 'qs';
export default {
	created() {
		//支付完成后会来到这个页面
		//需要获取订单是否支付成功
		//下面两个参数支付完成后跳转时支付宝会返回给你
		let data = {
			out_trade_no: this.$route.query.out_trade_no, //订单号
			trade_no: this.$route.query.trade_no, // 支付宝交易号
		};
		console.log(data);
		// 向后端请求查询订单是否完成
		axios({
			url: '/api/queryOrder',
			method: 'post',
			headers: { 'content-type': 'application/x-www-form-urlencoded' },
			data: qs.stringify(data),
		}).then((res) => {
			console.log(res);
		});
	},
};
</script>
