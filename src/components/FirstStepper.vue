<template>
    <div class="descriptionWrapper">
        <h3>{{this.title}}</h3>
        {{this.stepperData[this.activeTab].description}}
    </div>
    <ul class="stepperList">
        <li @click="changeActiveTab(index)"
            v-for="(step,index) in stepperData">
            <span :class="{stepperItem:true,activeItem:index<=activeTab}">{{index+1}}</span>
            <span>{{step.title}}</span>
        </li>
    </ul>
    <div class="buttonsWrapper">
        <button
                :class={disable:backDisabled,open:!backDisabled}
                :disabled="backDisabled"
                @click="backClick"
        >{{!start?"Начать заново":"Назад"}}
        </button>
        <button
                v-if='!isFinish'
                @click="forward">{{forwardDisabled && this.activeTab!==0? 'Закончить':'Вперед'}}
        </button>
    </div>
</template>

<script>
	//import
	export default {
		data() {
			return {
				title: "Изучение vue 3",
				activeTab: 0,
				backDisabled: true,
				forwardDisabled: false,
				isFinish: false,
				start: true,
				stepperData: [{
					title: 'Основы',
					description: `Являясь всего лишь частью общей картины, базовые сценарии поведения пользователей призывают нас к новым свершениям, которые, в свою очередь, должны быть рассмотрены исключительно в разрезе маркетинговых и финансовых предпосылок. В целом, конечно, курс на социально-ориентированный национальный проект предоставляет широкие возможности
                для поэтапного и последовательного развития общества.`
				}, {
					title: 'Компоненты',
					description: `В рамках спецификации современных стандартов, базовые сценарии поведения пользователей описаны максимально подробно. Являясь всего лишь частью общей картины, сделанные на базе интернет-аналитики выводы, превозмогая сложившуюся непростую экономическую ситуацию, указаны как претенденты на роль ключевых факторов.`
				}, {
					title: 'Роутер',
					description: `В своём стремлении повысить качество жизни, они забывают, что начало повседневной работы по формированию позиции однозначно определяет каждого участника как способного принимать собственные решения касаемо первоочередных требований. Как принято считать, элементы политического процесса представляют собой не что иное, как квинтэссенцию победы маркетинга над разумом и должны быть функционально разнесены на независимые элементы.`
				}, {
					title: 'Vuex',
					description: `Задача организации, в особенности же высококачественный прототип будущего проекта требует определения и уточнения системы массового участия.`
				}, {
					title: 'Composition',
					description: `В своём стремлении улучшить пользовательский опыт мы упускаем, что действия представителей оппозиции
									 формируют глобальную экономическую сеть и при этом — превращены в посмешище, хотя само их существование
									  приносит несомненную пользу обществу.`
				}],
				//	text: this.stepperData,
			}

		},
		methods: {
			backClick() {
				if (!this.start) {
					this.isFinish = false
					this.start = true
					this.activeTab = 0
				}
				else {
					this.changeActiveTab(this.activeTab -= 1)

				}
			},
			forward() {
				if (this.activeTab === this.stepperData.length - 1) {
					this.isFinish = true
					this.start = false
				}
				else {
					this.changeActiveTab(this.activeTab += 1)
				}
			},
			changeActiveTab(ind) {
				this.activeTab = ind
				this.backDisabled = this.activeTab === 0;
				this.forwardDisabled = this.activeTab === this.stepperData.length - 1
			}
		}
	}
</script>
<style scoped>
    .activeItem {
        background: #7c073c !important;
        color:wheat !important;
    }

    .descriptionWrapper {
        height: 200px;
        background: wheat;
    }

    .stepperList {
        display: grid;
        grid-template-columns: repeat(6, minmax(100px, 1fr));
        grid-auto-rows: 200px;
        gap: 10px;
        background: darkslategray;
        border-radius: 5px;
    }

    .stepperList li {
        list-style: none;
    }
    .stepperItem:first-child {
        width: 20px;
        height: 20px;
        display: inline-block;
        border-radius: 50%;
        background: aquamarine;
        color: #23418e;
        text-align: center;
    }

    .disable {
        background: red;
    }

    .open {
        background: green;
    }
</style>
