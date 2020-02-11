<template>
    <view>
        <view class="content">
            <mrpzx-checker-box ref="questionChecker" @on-change="onChange" :type="type" v-model="question.value" :class="{'item-selected': isCheck}">
                <view class="title">{{question.title}}</view>
                <mrpzx-checker-item @checkItem="contentClick" :iconType="iconType" :checked="false" :value="vo.id" index="question" v-for="(vo, index) in question.answer" :key="index">
                    <view class="answer">{{vo.title}}</view>
                    <view class="line"></view>
                </mrpzx-checker-item>
            </mrpzx-checker-box>
        </view>
        <view class="options">
            <mrpzx-checker-box @on-change="onOptionChange" :must="true" type="radio">
                <view class="title">选择类型</view>
                <mrpzx-checker-item :checked="true" value="radio" index="options">
                    <view class="answer">radio</view>
                    <view class="line"></view>
                </mrpzx-checker-item>
                <mrpzx-checker-item :checked="false" value="checkbox" index="options">
                    <view class="answer">checkbox</view>
                    <view class="line"></view>
                </mrpzx-checker-item>
            </mrpzx-checker-box>
        </view>
    </view>
</template>

<script>
	export default {
		data() {
			return {
                type: 'radio',
                isCheck: !1,
				question: {
                    title: '您的年龄是？',
                    value: 0,
                    answer: [{
                        id: 1,
                        title: '25岁以下（含）'
                    },{
                        id: 2,
                        title: '26-35岁'
                    },{
                        id: 3,
                        title: '36-45岁'
                    },{
                        id: 4,
                        title: '46-55岁'
                    },{
                        id: 5,
                        title: '56岁以上'
                    }]
                }
			}
		},
        computed: {
            iconType () {
                return this.type == 'radio' ? 'circle' : 'box'
            }
        },
		methods: {
            contentClick (isCheck, index, value) {
                this.isCheck = isCheck
                console.log('isCheck: ' + isCheck + "\n" + 'index: ' + index + "\n" + 'value:' + value)
                console.log((isCheck ? '选中了：' : '取消选中') + value)
                console.log('question.value: ' + JSON.stringify(this.question.value))
            },
            onChange (value, isCheck) {
                console.log('changed: ' + JSON.stringify([value, isCheck]))
            },
            onOptionChange (value, isCheck) {
                if (value !== this.type) {
                    this.$refs.questionChecker.clearCheck()
                }
                this.type = value
            }
		}
	}
</script>

<style>
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
    
    .checker-box .checker-item .answer {
        display: inline-block;
        padding: 48rpx 0;
        font-size: 32rpx;
        line-height: 44rpx;
        width: 92%
    }
    
    .checker-box .item-selected .checker-item-tag .answer {
        color: #2e5bff;
        font-weight: 700
    }
</style>
