<template>
	<view style="height: 10%;">
		<!-- <HeaderUse/> -->
		<!-- 签收回单 -->
		<uni-row>
			<uni-col :span="5">
				<button class="littleUseButtonAll"
					style="background-color: #F1F1F1;color: #3B4144;margin-left: 20rpx;margin-top: 10rpx;margin-bottom: 10rpx;width: 150rpx;">司机交单</button>
			</uni-col>
			<uni-col :span="14">
				<button class="littleUseButtonAll" @click="dcClick"
					style="margin-left: 20rpx;margin-top: 10rpx;margin-bottom: 10rpx; width: 150rpx;">送交客户</button>
			</uni-col>
			<uni-col :span="5">
				<button class="littleUseButtonAll" @click="historySearch"
					style="margin-left: 20rpx;margin-top: 10rpx;margin-bottom: 10rpx;">历史查询</button>
			</uni-col>
		</uni-row>
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
				<button class="littleUseButtonAll" @click="searchUse" ref="client">搜索</button>
			</uni-col>
		</uni-row>
		
		<uni-card style="margin-top: 10rpx;">
			<!-- <uni-table type="selection" @selection-change="change" border stripe emptyText="暂无更多数据"
			 :loading="false">
			<uni-tr v-show="true">
				<uni-th align="center" v-for="i,k in header"  :width="i.length>3?60:30" :key="k" >{{i}}</uni-th>
			</uni-tr>
			<uni-tr v-show="false">
				
			</uni-tr>
			</uni-table>
			 -->
			<uni-table type="selection" @selection-change="change" border stripe emptyText="暂无更多数据"
			:stripe="true"
			:style="useTableStyle">
				<!-- 表头行 -->
				<uni-tr v-show="true">
					<uni-th align="center" v-for="i,k in header" :width="i.length>2?40:2" :key="k" >{{i}}</uni-th>
				</uni-tr>
				<!-- 表格数据行 -->
				<uni-tr v-for="j,nu in listSecond" :key="nu" :disabled="j['pz']=='已拍'?false:true">
					<uni-td v-for="w,index in listSecond[0]"    v-if="index!='pz'" >
						{{j[index]}}
					</uni-td>
					<uni-td :key="120" width="40">
						<uni-tag size="normal" style="width: 5rpx;" inverted="true" :text="j['pz']" 
							:type="j['pz']=='已拍'?'primary':'error'" @click="definePhoto(nu,j['pz'])"></uni-tag>
					</uni-td>
					<!-- <uni-td :key="120"><button @click="use(j)" style="width: 120rpx;font-size: small;color: #FFFAFA; background-color: rgba(49, 139, 74, 1)">编辑</button></uni-td>
	 -->
				</uni-tr>


			</uni-table>
			<!-- table2 -->

		</uni-card>
		<view style="padding-left: 32%; padding-top: 15rpx;"><text
				style="color: #606266;padding-right: 12rpx;">累计:</text><label
				style="background-color: #F0F0F0; padding: 8rpx 50rpx 12rpx 50rpx;">{{chooseNum}}</label><text
				style="color: #606266">份</text>
		</view>
		<view>
			<button :disabled="chooseNum>0?false:true" @click=" " class="info position-sticky fixed-bottom">签收</button>
			<button type="default" @click="" class="info position-sticky fixed-bottom2" ref="hddcClient">回单导出</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				listThird: [{}],
				carOrgoodsNum: '',
				chooseNum: 0,
				tableHeight:'',
				totalContent: 100,
				// styleUse:{height: '100%'},
				datetime: '',
				header: ['日期车号', '交货单号', '数量', '起点', '讫点', '单位', '拍照'],
				listSecond: [],
				list: [{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					}, {
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "补拍",

					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					}, {
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					}, {
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					},
					{
						rqch: "2022/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "12",
						dw: "垛",
						pz: "已拍",

					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					},

				]

			}
		},
		computed:{
			useTableStyle(){
				return "max-height:" + this.tableHeight + 'px'
			}
			
		},
		mounted() {
			this.listSecond = this.list
			// this.tableHeight = this.$refs.hddcClient.$el.getBoundingClientRect().top-this.$refs.client.$el.getBoundingClientRect().bottom-30
			console.log("这是"+this.tableHeight)
			uni.getSystemInfo({
				success:(res)=> {
					console.log(res.windowHeight)
					this.tableHeight = res.windowHeight - 200
					console.log(this.tableHeight)
					
				}
			})
			
		},
		methods: {
			 
			change(e) {
				console.log(e)
				this.chooseNum = e.detail.index.length
				let k = 0
				for (let i in this.list) {
					for (let j in e.detail.index) {
						if (i == j) {
							this.listThird[k] = this.list[i]
							k++
						}

					}
				}


				console.log(this.listThird)
			},
			use(e) {
				console.log(e)

			},
			dcClick() {
				uni.navigateTo({
					url:"./sjkh"
				})

			},
			definePhoto(e, data) {
				if (data == "补拍") {
					console.log(e, data)
					uni.chooseImage({
						count: 9,
						sizeType: ['original', 'compressed'],
						sourceType: ['camera'], //这要注意，camera掉拍照，album是打开手机相册
						success: (res) => {
							// console.log(res);
							// const tempFilePaths = res.tempFilePaths;
							// this.zp = res.tempFilePaths[0];
							// console.log(this.zp)
							this.list.push(res.tempFilePaths[0])
							console.log(res.tempFilePaths[0])
							// console.log(this.list)

						}
					});
				}

			},
			historySearch(){
				uni.navigateTo({
					url:"./hdqs"
				})
			},
			searchUse() {
				// console.log(this.datetimerange[0].replaceAll("-","/"))
				// if (this.datetimerange=='' || this.carOrgoodsNum.length<=0) {
				// 	this.list = this.listSecond
				// }else{
				this.listSecond = this.list.filter( //便编写的查询过滤器考虑把次放出去因为每个的页面需要的过滤属性不一样
					(data) =>
					!this.carOrgoodsNum ||
					(data['rqch'] + "")
					.toLowerCase()
					.includes(this.carOrgoodsNum.toLowerCase()) || (data['jhdh'] + "")
					.toLowerCase()
					.includes(this.carOrgoodsNum.toLowerCase())

				).filter(
					data => !this.datetime ||
					(data['rqch'] + "")
					.toLowerCase()
					.includes(this.datetime.replaceAll("-", "/").toLowerCase())

				)
				// .filter(data => !this.datetimerange[1] ||
				// 	(data['rqch'] + "")
				// 	.toLowerCase()
				// 	.includes(this.datetimerange[1].replaceAll("-", "/").toLowerCase()));
				// }


			}
		}
	}
</script>

<style>
	.uni-input-placeholder {
		font-size: xx-small !important;
	}

	.uni-input-input {
		font-size: xx-small !important;
	}

	/* 	/deep/ .uni-date-x.uni-date-range {
		height: 57rpx;
	} */
	/deep/ .uni-date-x.uni-date-single {
		height: 57rpx;
	}


	/deep/ .uni-easyinput__content.is-input-border {
		height: 60rpx !important;
		min-height: 0;
	}

	.position-sticky {
		position: -webkit-sticky !important;
		position: sticky !important;
	}

	.fixed-bottom {
		position: fixed !important;
		height: 80rpx;
		margin-left: 0;
		background-color: rgba(49, 139, 74, 1);
		font-size: large;
		color: #FFFAFA;
		right: 0;
		bottom: calc(var(--window-bottom) + 3px);
		left: 0;
	}

	.fixed-bottom2 {
		position: fixed !important;
		width: 80px;
		height: 30px;
		margin-right: 10rpx;
		background-color: rgba(49, 139, 74, 1);
		font-size: small;
		color: #FFFAFA;
		right: 0;
		bottom: calc(var(--window-bottom) + 120rpx);
		left: 0;
	
	}

	.fixed-bottom3 {
		position: fixed !important;
		margin-right: 10rpx;
		font-size: small;
		right: 0;
		bottom: calc(var(--window-bottom) + 180rpx);
		left: 0;
	}

	.uni-card.uni-border {
		/* max-height: 1000px; */
		margin: 0;
	}

	.littleUseButtonAll {
		padding: 0;
		height: 60rpx;
		font-size: smaller;
		background-color: rgba(49, 139, 74, 1);
		color: #FFFAFA;

	}

	/deep/ .uni-date__icon-clear {
		margin-top: -12rpx !important;

	}
	.uni-table-td{
		word-wrap: break-word;
		word-break: break-all;
		font-size: 1px;
		padding: 0;

	}
	/deep/.checkbox.tr-table--border{
		width: 2px !important;
	}
	.uni-table-th.table--border{
		padding: 0;
	}
</style>

<!-- style="padding: 0; height: 60rpx; font-size: smaller;background-color: rgba(49, 139, 74, 1);color: #FFFAFA;" -->
