<template>
	<view class="buyingContainer">
		<vue-falls :photoList="photoList" width="500"></vue-falls>
	</view>
</template>

<script>
	import buyingInfo from '../../utils/request.js'
	
	export default {
		data() {
			return {
				saleGoods: {},
				photoList: ["https://yanxuan.nosdn.127.net/e72e29b81e2178a4ee98b25da5898265.jpg"]
			}
		},
		mounted() {
			
		},
		methods: {
			async getBuyingInfo() {
				const res = await request('/getBuyingData')
				if(res.code === 200) {
					this.saleGoods = res.data.result
				}
			}
		}
	}
</script>

<style lang="stylus">
</style>
