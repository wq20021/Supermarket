<template>
	<view class="page">
	<view class="content">
		<swiper class="content" :autoplay="true" :interval=3000 >
			<swiper-item v-for="(img, index) in wheel" :key="index">
				<image :src="'http://www.kupai666.com/static/goods/index_img/' + img.wheel_img" class="swiper-img"></image>
			</swiper-item>
		</swiper>
		   <view class="page-body">
			   <view class="navigation-title" v-for="(im, imgindex) in navigation" :key="imgindex">
		                <navigator url="#" class="navigation">
							<image :src="'http://www.kupai666.com/static/goods/index_img/' +im.navigation_img" class="navigation-img"></image>
		                    <view class="navigation-but">{{ im.navigation_name}}</view>
		                </navigator>
				</view>
		    </view>
	</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				wheel: [],
				navigation: [],
			}
		},
		onLoad() {
			uni.request({
				url:'http://www.kupai666.com/index/',
				success: (res) => {
					this.wheel = res.data.data.wheel
					this.navigation = res.data.data.navigation
				}
			})

		},
		methods: {

		}
	}
</script>

<style>
@import url("index.css");
</style>
