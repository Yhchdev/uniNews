<template>
	<view class="content">
		<view class="title">{{title}}</view>
		<view class="art-content">
			<rich-text class="richText" :nodes="strings"></rich-text>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title:'',
				strings:''
			}
		},
		methods: {
			onLoad(e){
				//console.log(e);
				uni.request({
					url: 'https://unidemo.dcloud.net.cn/api/news/36kr/' +e.newsid,
					method: 'GET',
					data: {},
					success: res => {
						this.title = res.data.title
						this.strings = res.data.content
						//console.log(res)
					},
					fail: () => {},
					complete: () => {}
				});
			}
			
		}
	}
</script>

<style>
	.content{padding: 1em 3%; width: 94%; flex-wrap: wrap;}
	.title{line-height: 2em; font-weight: 700 ;font-size: 38upx;}
	.art-content{line-height: 2em;}

</style>
