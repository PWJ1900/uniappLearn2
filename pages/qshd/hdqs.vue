<template>
	<view>
		<view>
			<uni-row>
				<uni-col :span="8">
					<uni-easyinput id="use" v-model="carOrgoodsNum" placeholder="输入交货号或车号">
					</uni-easyinput>
				</uni-col>
				<uni-col :span="12">
					<!-- <input type="text" placeholder="起止时间"/> -->
					<view class="example-body">
						<uni-datetime-picker v-model="datetime" type="date" />
					</view>
				</uni-col>
				<uni-col :span="4">
					<button class="littleUseButtonAll" @click="searchUse">搜索</button>
				</uni-col>
			</uni-row>
			<uni-card note="true" style="height: 190rpx; padding: 0 !important;">
				<uni-row>
					<uni-col :span="19">
						<text style="font-size: smaller;">客户签收</text>
					</uni-col>
					<uni-col :span="5">
						<text style="font-size: smaller;">5月25日</text>
					</uni-col>

				</uni-row>
				<uni-row style="margin-bottom: 0;">
					<uni-col :span="20">
						<text style="font-size: larger;" space="emsp">{{list.length}}</text>份
					</uni-col>
					<uni-col :span="4">
						<uni-icons type="forward" size="30" @click="tableTo()"></uni-icons>
					</uni-col>
				</uni-row>

				<template v-slot:footer>
					<view class="footer-box">

					</view>
				</template>
			</uni-card>
			<!-- <button style="width: 200rpx;font-size: smaller;margin-right: 0;" @click="popShare">分享</button> -->
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				datetime: '',
				
				carOrgoodsNum: '',
				listUse: [],
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
				
			}	
		},
		methods: {
			tableTo(){
				uni.navigateTo({
					url:"./historySearch"
				})
				
			},
			searchUse() {
				let colorUse = []
				let listUseTwo = this.list.filter( //便编写的查询过滤器考虑把次放出去因为每个的页面需要的过滤属性不一样
					(data) =>
					!this.carOrgoodsNum ||
					(data['rqch'] + "")
					.toLowerCase()
					.includes(this.carOrgoodsNum.toLowerCase()) ||
					(data['jhdh'] + "")
					.toLowerCase()
					.includes(this.carOrgoodsNum.toLowerCase())

				).filter(
					data => !this.datetime ||
					(data['rqch'] + "")
					.toLowerCase()
					.includes(this.datetime.replaceAll("-", "/").toLowerCase())

				)
				for (let i in listUseTwo) {
					colorUse.push(this.list.indexOf(listUseTwo[i]))

				}
				uni.navigateTo({
					url:"./historySearch?item="+encodeURIComponent(JSON.stringify(colorUse))
				})
			}

		}
	}
</script>

<style>
	.littleUseButtonAll {
		padding: 0;
		height: 60rpx;
		font-size: smaller;
		background-color: rgba(49, 139, 74, 1);
		color: #FFFAFA;
	}

	.uni-input-placeholder {
		font-size: xx-small !important;
	}

	.uni-input-input {
		font-size: xx-small !important;
	}

	/deep/ .uni-date-x.uni-date-single {
		height: 57rpx;
	}


	/deep/ .uni-easyinput__content.is-input-border {
		height: 60rpx !important;
		min-height: 0;
	}

	/deep/ .uni-date__icon-clear {
		margin-top: -12rpx !important;

	}
</style>
