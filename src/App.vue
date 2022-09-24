<template>
    <!--    <first-stepper></first-stepper>-->
    <resume-creator></resume-creator>
</template>

<script>
	import FirstStepper from './components/FirstStepper.vue'
	import ResumeCreator from './components/Resume/ResumeCreator.vue'

	export default {
		components: {'first-stepper': FirstStepper,'resume-creator':ResumeCreator}
	}
</script>
<style scoped>

</style>
