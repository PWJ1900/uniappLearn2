<template>
	<view>
		<uni-card style="margin-top: 10rpx;">
			<uni-table type="selection" @selection-change="change" border stripe emptyText="暂无更多数据"
				:style="useTableStyle" :key="1">
				<!-- 表头行 -->
				<uni-tr>
					<uni-th align="center" v-for="i,k in header" width="10" :key="k">{{i}}</uni-th>
				</uni-tr>
				<!-- 表格数据行 -->
				<uni-tr v-for="j,nu in list" :key="nu"
					:style="colorIndex.includes(nu)?`background-color: #4CD964;`:``">
					<uni-td v-for="w,index in list[0]" width="40" style="height: 10rpx;" v-if="index!='pz'">
						{{j[index]}}
					</uni-td>
					<uni-td :key="120">
						<uni-tag size="normal" style="width: 60rpx;" inverted="true" :text="j['pz']"
							:type="j['pz']=='已拍'?'primary':'error'"></uni-tag>
					</uni-td>
				</uni-tr>


			</uni-table>
			<!-- table2 -->

		</uni-card>
		<button style="width: 200rpx;font-size: smaller;margin-right: 0;" @click="popShare()">分享</button>

	</view>
</template>

<script>
	export default {
		onLoad(option) {
			if(option.item)
			this.colorIndex = JSON.parse(decodeURIComponent(option.item))
		},
		data() {
			return {
				colorIndex: [],
				tableHeight:'',
				listUse:[{}],
				header: ['日期车号', '交货单号', '数量', '起点', '讫点 ', '单位 ', '签收日期 '],
				list: [{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					}, {
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					}, {
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					}, {
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
					{
						rqch: "2022/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "12",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646481",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
				
				]
					}},
					computed:{
						useTableStyle(){
							return "max-height:" + this.tableHeight + 'px'
						}
						
					},
					mounted() {
						uni.getSystemInfo({
							success:(res)=> {
								console.log(res.windowHeight)
								this.tableHeight = res.windowHeight - 150
								console.log(this.tableHeight)
								
							}
						})
					},
				methods: {
					change(e){
						console.log(e)
						
					},
					popShare() {
						 plus.share.sendWithSystem({content:'分享内容',href:'https://www.dcloud.io/'}, function(){
						        console.log('分享成功');
						    }, function(e){
						        console.log('分享失败：'+JSON.stringify(e));
						    });
						// uni.share({
						// 	provider: "weixin",
						// 	scene: "WXSceneSession",
						// 	type: 1,
						// 	summary: "我正在使用HBuilderX开发uni-app，赶紧跟我一起来体验！",
						// 	success: function(res) {
						// 		console.log("success:" + JSON.stringify(res));
						// 	},
						// 	fail: function(err) {
						// 		console.log("fail:" + JSON.stringify(err));
						// 	}
						// });
					
					},

				}
			}
</script>

<style>

</style>
