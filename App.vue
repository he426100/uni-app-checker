<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
    @import 'static/css/iconfont.css';
    
    .checker-box {
        background-color: #fff;
        min-height: 900rpx;
        -webkit-box-shadow: 0 2px 4px 0 #e5e5e5;
        box-shadow: 0 2px 4px 0 #e5e5e5;
        border-radius: 8rpx
    }
    
    .checker-box .title {
        padding: 42rpx 0 40rpx;
        font-size: 40rpx;
        font-weight: 700;
        color: #33353f;
        margin: 0 38rpx;
        max-height: 190rpx;
        line-height: 54rpx;
        -webkit-box-sizing: border-box;
        box-sizing: border-box
    }
    
    .checker-box .checker-item {
        position: relative;
        padding: 0 38rpx
    }
    
    .checker-box .checker-item .answer {
        display: inline-block;
        padding: 48rpx 0;
        font-size: 32rpx;
        line-height: 44rpx;
        width: 92%
    }
    
    .checker-box .checker-item:active {
        background-color: #f2f4f6;
        font-weight: 700
    }
    
    .checker-box .checker-icon {
        position: absolute;
        right: 30rpx;
        top: 45rpx
    }
    
    .checker-box .item-selected .checker-item-tag .answer {
        color: #2e5bff;
        font-weight: 700
    }
</style>
