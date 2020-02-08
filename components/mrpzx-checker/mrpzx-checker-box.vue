<template>
	<view class="checker-box">
		<slot />
	</view>
</template>

<script>
	export default {
		name: "checker",
        props: {
            value: {
                default: ""
            },
            type: {
                type: String,
                default: "radio"
            }
        },
        data () {
            return {
                hashCache: {} // {'a': true, 'b': false, ...}
            }
        },
        provide() {
        	return {
        		checker: this
        	}
        },
        created() {
        	this.childrens = []
        },
        methods: {
            /**
             * @param {Object} value radio时value为单个值，如 xxx，checkbox时为对象，如 {'xxx': true}
             * @param {Object} isCheck 是否选中
             */
            changeHandler (value, isCheck) {
                if ("radio" === this.type)
                    this.$emit("input", value),
                    this.$emit("on-change", value, isCheck),
                    this.childrens.forEach((item, index) => {
                        if (item.isCheck && value !== item.value) {
                            item.isCheck = false
                        }
                    })
                else if ("checkbox" === this.type) {
                    Object.assign(this.hashCache, value);
                    let i = this.parseHashCache();
                    this.$emit("input", i),
                    this.$emit("on-change", i)
                }
            },
            clearCheck () {
                this.childrens.forEach((item, index) => {
                    if (item.isCheck) {
                        item.isCheck = false
                        this.hashCache[item.value] = false
                    }
                })
                let e = this.parseHashCache();
                this.$emit("update:value", e),
                this.$emit("on-change", e)
            },
            clear () {
                this.childrens.forEach((item, index) => {
                    if (item.isCheck) {
                        this.hashCache[item.value] = true
                    }
                })
                let e = this.parseHashCache();
                this.$emit("update:value", e)
            },
            checkAll () {
                this.childrens.forEach((item, index) => {
                    if (item.isCheck) {
                        this.hashCache[item.value] = true
                    }
                })
                let e = this.parseHashCache();
                this.$emit("update:value", e),
                this.$emit("on-change", e)
            },
            parseHashCache () {
                let t = [];
                for (let e in this.hashCache) {
                    if (!0 === this.hashCache[e]) {
                        t.push(e)
                    }
                }
                return t
            }
        }
	}
</script>
