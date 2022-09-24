<template>
    <div class="contentWrapper">
        <creation-block @addData="addData"></creation-block>
        <result-block :components="componentsData"></result-block>
    </div>
</template>

<script>
	import CreationBlock from "./CreationBlock.vue";
	import ResultBlock from "./ResultBlock.vue";

	export default {
		data() {
			return {
			componentsData:[]
			}
		},
		components: {'creation-block': CreationBlock, 'result-block': ResultBlock},
		methods: {
			addData(type, data) {
				this.componentsData=[...this.componentsData,{type:type,data:data}]
			}
		}
	}
</script>
<style scoped>

    .contentWrapper {
        width: 500px;
        height: 500px;
        background-color: goldenrod;
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-around;
    }
</style>