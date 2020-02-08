**插件使用说明**

- 支持radio和checkbox，支持双向绑定，测试过App和H5
- 基于 vant-checker，修改以适用于uni-app
- 组件逻辑参考uni-uni-collapse

### 1.基本用法

```
<template>
	<view class="content">
		<mrpzx-checker-box @on-change="onChange" :type="type" v-model="question.model" :class="{'item-selected': isCheck}">
		    <view class="title">{{question.title}}</view>
		    <mrpzx-checker-item @checkItem="contentClick" :checked="false" :value="vo.id" :index="questionIndex" v-for="(vo, index) in question.answer" :key="index">
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
                if (this.type == 'type') {
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
```

### 2.更多用法
请查看源码

### 3.参数说明

### checker-box props
| 参数           | 说明            | 类型    | 可选值     | 默认值  |    
| :-------------------- | :------------------------------ | :---------- | :-------- | :--- |  
| v-model | 选中值 | - | - | - |
| type | 类型 | string | radio/checkbox | radio |

### checker-box events
| name | 说明 | 回调参数 |
| :--- | :---------------- | ------------------|
| on-change | 选中状态发生变更 | 更新后选中值的value组 |

### checker-item props
| 参数           | 说明            | 类型    | 可选值     | 默认值  |    
| :-------------------- | :------------------------------ | :---------- | :-------- | :--- |  
| value | 值 | - | - | - |
| index | 问题索引 | number | - | - |
| height | 高度 | - | - | - | - |
| width | 宽度 | - | - | - |
| iconType | 图标类型 | string | circle/box | circle |
| checked | 是否选中 | boolean | true/false | false |

### checker-item events
| name | 说明 | 回调参数 |
| :--- | :---------------- | ------------------|
| checkItem | 选中状态发生变更 | isCheck, index, value |
