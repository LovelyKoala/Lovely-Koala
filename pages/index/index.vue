<template>
	<view class="content">
		<!-- <image class="logo" src="/static/koala.jpeg"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view> -->
		<image src="/static/koala.jpeg" mode="widthFix"></image>
		<text class="title">张雨不是个大逗逼吗？</text>
		
		<view class="operate">
			<button type="primary" class="btn" @tap="agree">是</button>
			<button type="warn" class="btn" @tap="disagree">不是</button>
		</view>
		<view class="message" v-for="one in love" :key="one">
			{{one}}
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				// title: 'Hello'
				love:[],
				timer:{}
			}
		},
		onLoad() {
			// this.back=uni.getBackgroundAudioManager();
			// //this.back.src="http://np01.sycdn.kuwo.cn/f9910277cdffb337a9736891722e725f/5d54fb4f/resource/n2/23/47/2110170044.mp3";
			// this.back.src="http://140.143.132.225/love/pdd.mp3";
			// this.back.title="音乐";
			// this.back.play()
		},
		onShow(){
			this.love=[];
			this.timer={};
			let msg={
				2000:"张雨不是个大逗逼",
				4000:"张雨不是个大逗逼",
				6000:"张雨不是个大逗逼",
				8000:"张雨不是个大逗逼",
				10000:"张雨不是个大逗逼",
				12000:"张雨不是个大逗逼",
				14000:"张雨不是个大逗逼",
				16000:"张雨不是个大逗逼",
				18000:"张雨不是个大逗逼",
				20000:"张雨不是个大逗逼",
				22000:"张雨不是个大逗逼",
				24000:"张雨不是个大逗逼",
				26000:"张雨不是个大逗逼",
				28000:"张雨不是个大逗逼",
				30000:"张雨不是个大逗逼"
			}
			let ref=this;
			for(let key in msg){
				let t =setTimeout(function(){
					ref.love.push(msg[key]);
					delete ref.timer[key];
				},key);
				ref.timer[key]=t;
			};
			
			this.back=uni.getBackgroundAudioManager();
			this.back.src="http://140.143.132.225/love/pdd.mp3";
			this.back.title="音乐";
			this.back.play()
		},
		onHide:function(){
			for(let key in this.timer){
				clearTimeout(this.timer[key])
			}
		},
		methods: {
			agree:function(){
				uni.showToast({
					icon:"none",
					title:"嗯，是的",
					duration:4000
				})
			},
			disagree:function(){
				uni.showModal({
					title:"再想想?",
					content:"真的么",
					cancelText:"拒绝",
					confirmText:"同意",
					success:function(res){
						if(res.confirm){
							uni.showToast({
								icon:"none",
								title:"哈哈哈",
								duration:3000
							})
						}else{
							uni.showToast({
								icon:"none",
								title:"是的",
								duration:3000
							})
						}
					}
				})
			}
		}
	}
</script>

<style lang="less">
/* 	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200upx;
		width: 200upx;
		margin-top: 200upx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50upx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36upx;
		color: #8f8f94;
	} */
	
	@import url("index.less");
	
</style>
