<template>
	<view class="indexContainer">
		<!-- 头部搜索区域 -->
		<view class="header">
			<image class="logo" src="../../static/images/logo.png" mode=""></image>
			<view class="search">
				<view class="iconfont icon-sousuo"></view>
				<input class="searchInput" type="text" placeholder-class="placeholder" placeholder="搜索商品" />
			</view>
			<button class="btn" type="default">Gin</button>
		</view>
		<!-- navbar区域 -->
		<scroll-view class="navbar" scroll-x v-if="kingKong.kingKongModule">
			<view class="nav-item active">推荐</view>
			<view class="nav-item" 
				v-for="item in kingKong.kingKongModule.kingKongList" 
				:key="item.L1Id">{{item.text}}</view>
		</scroll-view>
	</view>
</template>

<script>
	import request from '../../utils/request.js'
	
	export default {
		data() {
			return {
				kingKong: {}
			}
		},
		async mounted() {
			const res = await request('/getHomeData')
			if(!res) {
				this.kingKong = {
					"kingKongModule": {
						"kingKongList": [
							{
							  "text": "居家生活",
								"L1Id": 111
							},
							{
							  "text": "服饰鞋包",
								"L1Id": 222
							},
							{
							  "text": "美食酒水",
								"L1Id": 333
							}
						]
					}
				}
			}else {
				this.kingKong = res.data
			}
		}
	}
</script>

<style lang="stylus">
	.indexContainer
		.header
			display flex
			align-items center
			margin-top 20upx
			.logo
				margin 0 20upx
				flex-shrink 0
				width 140upx 
				height 40upx
			.search
				position relative
				flex-grow 1
				height 60upx
				background-color #ededed
				border-radius 10upx
				.searchInput
					padding-left 64upx
					height 100%
					line-height 60upx
				.placeholder
					line-height 60upx
					text-indent -64upx
					font-size 24upx
					text-align center
				.icon-sousuo
					position absolute
					top 50%
					padding-left 20upx
					transform translateY(-50%)
			.btn 
				margin 0 20upx
				flex-shrink 0
				width 144upx
				height 60upx
				line-height 60upx
				color #b4282d
		.navbar
			white-space nowrap
			.nav-item
				display inline-block
				margin 0 10upx
				width 140upx
				height 80upx
				text-align center
				line-height 80upx
				font-size 28upx
				&.active
					border-bottom 2upx solid #B4282D
</style>
