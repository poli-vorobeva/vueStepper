<template>
    <div class="wrapper">
        <div v-for="c in components">
            <h2 v-if="c.type==='title'">{{c.data}}</h2>
            <p v-if="c.type==='text'">{{c.data}}</p>
            <ul v-if="c.type==='list'">
                <li v-for="c in this.listData(c.data)">{{c}}</li>
            </ul>
            <img v-if="c.type==='avatar'" :src="c.data" alt="">
        </div>
    </div>
</template>

<script>
	export default {
		props: ['components'],
      methods:{
			listData(data){
			return data.split('\n')
            }
      }
	}
</script>

<style scoped>
    .wrapper {
        width: 300px;
        height: 100%;
        background-color: salmon;
        display: flex;
        flex-flow: column nowrap;
        justify-content: space-evenly;
        align-items: center;
    }
    img{
        width: 50px;
        height: 50px;
        border-radius:50%;
    }
</style>