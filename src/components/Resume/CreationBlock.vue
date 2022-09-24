<template>
    <div class="wrapper">
        <select name="createType" id="" v-model="creationType">
            <option value="title">Заголовок</option>
            <option value="avatar">Картинка</option>
            <option value="text">Текст</option>
            <option value="list">Список</option>
        </select>
        <textarea v-model="textAreaValue" rows="10"></textarea>
        <button @click="addData">Add</button>
    </div>
</template>

<script>
	export default {
		emits:['addData'],
		data() {
					return {
						creationType: null,
						textAreaValue: null
					}
				},
		methods:{
			addData(){
				this.$emit('addData',this.creationType,this.textAreaValue)
              this.creationType=null
              this.textAreaValue=null
          }
        }
	}
</script>

<style scoped>
    .wrapper {
        width: 150px;
        height: 100%;
        background: cornflowerblue;
    }
    textarea{
        width: 113px;
        height: 94px;
        resize: none;
        border-radius: 5px;
        border: none;
        outline: none;
        box-shadow: 0 0 5px -1px #6842ac
    }
</style>