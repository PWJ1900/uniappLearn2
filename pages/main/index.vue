<template>
	<view>
		<!-- <HeaderUse></HeaderUse>
		<htcz v-if='pageUse["usehtcz"]'></htcz>
		<sqzj v-if='pageUse["usesqzj"]'></sqzj>
		<qshd v-if='pageUse["useqshd"]'></qshd> -->
		<!-- @SearchReturn="defineSearch" -->
		<!-- 	<xzcl v-if='pageUse["usexzcl"]'></xzcl>
		<zfzj v-if='pageUse["usezfzj"]'></zfzj>
		<index v-if='pageUse["useindex"]'></index> -->
		<view> sdf </view>
		<view style="width: 710rpx;margin: 20rpx;">
			<uni-card>
			<uni-grid :column="3" :showBorder="true" :square="true" style="text-align: center;" @change="jump">
				<uni-grid-item v-for="i,index in tabsUse" style="" :index="index">
					<image style="background-size: 100% 100%;width: 30px;
		height: 30px;
		margin-left: 90rpx;
		margin-bottom: 20rpx;
		margin-top: 80rpx;" src="../../static/DE35DD80D8D46E56E74F9A41C81BC0CB.png"></image>
					<text class="text">{{i.name}}</text>
				</uni-grid-item>
			</uni-grid>
			</uni-card>
		</view>
	</view>
</template>

<script>
	import {
		mapState,
		mapGetters,
		mapMutations
	} from 'vuex'
	export default {
		data() {
			return {
				gettranToqshd: false
				// usehtcz:false,
				//    usesqzj:false,
				//    useqshd:false,
				//    usesqzj:false,
				//    usexzcl:false,
				//    usezfzj:false,
				//    useindex:true

			}

		},
		computed: {
			...mapState(["tabsUse"])
		},
		methods: {
			jump(e) {
				uni.navigateTo({
					url: this.tabsUse[e.detail.index].path
				})
				// console.log(e)
			}
			// defineSearch(e){
			// 	this.gettranToqshd = e			
			// }


		},
	}
</script>

<style>

</style>
