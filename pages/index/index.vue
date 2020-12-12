bdwwa<template>
	<view class="content">
		<view class="page-section page-section-gap">
			<map :id=currentMapId style="width: 100%; height: 300px;" :latitude="latitude" :longitude="longitude" :markers="covers">
			</map>
		</view>
		
		<view>
			<button @click="adjustThis">定位到您当前位置</button>
		</view>
		
		<view>
			<view>当前经度:{{ longitude }}</view>
			<view>当前维度:{{ latitude }}</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				currentMapId:"1",
				latitude: 39.909,
				longitude: 116.39742,
				covers: [{
					latitude: 39.909,
					longitude: 116.39742,
					iconPath: '../../../static/location.png'
				}, {
					latitude: 39.90,
					longitude: 116.39,
					iconPath: '../../../static/location.png'
				}]
			}
		},methods:{
			adjust( longitude , latitude ){
				this.latitude = latitude;
				this.longitude = longitude;
			},adjustThis(){
				let app = this;
				uni.getLocation({
					success: (res) => {
						let longitude = res.longitude;
						let latitude = res.latitude;
						app.adjust( longitude , latitude )
					}
				})
			}
		},onLoad() {

		}
	}
</script>

<style>

</style>
