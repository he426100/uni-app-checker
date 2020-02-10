<template>
	<view class="content">
		<mrpzx-checker-box @on-change="onChange" :type="type" v-model="question.model" :class="{'item-selected': isCheck}">
		    <view class="title">{{question.title}}</view>
		    <mrpzx-checker-item @checkItem="contentClick" iconType="circle" :checked="false" :value="vo.id" :index="questionIndex" v-for="(vo, index) in question.answer" :key="index">
		        <view class="answer">{{vo.title}}</view>
		        <view class="line"></view>
		    </mrpzx-checker-item>
		</mrpzx-checker-box>
	</view>
</template>

<script>
    import mrpzxCheckerBox from '@/components/mrpzx-checker/mrpzx-checker-box.vue'
    import mrpzxCheckerItem from '@/components/mrpzx-checker/mrpzx-checker-item.vue'

	export default {
        components: { mrpzxCheckerBox, mrpzxCheckerItem },
		data() {
			return {
                type: 'radio',
                isCheck: !1,
				question: {
                    title: '您的年龄是？',
                    model: 0,
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
                },
                questionIndex: 0 //标识问题索引（用于多个问题的场景）
			}
		},
		methods: {
            contentClick (isCheck, index, value) {
                this.isCheck = isCheck
                if (this.type == 'radio') {
                    console.log('isCheck: ' + isCheck + "\n" + 'index: ' + index + "\n" + 'value:' + value)
                    console.log('选中了：' + this.question.model)
                } else {
                    console.log('isCheck: ' + isCheck + "\n" + 'index: ' + index)
                    console.log(this.question.model)
                }
            },
            onChange (e) {
                console.log(e)
            }
		}
	}
</script>

<style>
	.content {
		
	}
</style>
