<template>
	<div v-for="header of headers" :key="header">{{ header }}</div>
</template>

<script setup>
	import { computed } from "vue"
	import { useRoute } from "vue-router"

	const route = useRoute()

	const headers = computed(() => {
		const firstCols = ["#", "Family Name"]

		switch (route.params.discipline) {
			case "contribution": return [...firstCols, null, "CP"]
			case "level":        return [...firstCols, "Character", "Level"]
			case "combat":       return [...firstCols, null, "Combat Fame"]
			case "life":         return [...firstCols, null, "Life Fame"]
			case "characters":   return [...firstCols, null, "Characters"]
			case "age":          return [...firstCols, null, "Age"]
			default:             return [...firstCols, "Character", "Rank"]
		}
	})
</script>

<style scoped>
	#leaderboard > * {
		padding: 0.5rem;
	}

	div {
		font-weight: bold;
	}

	div:first-child, div:nth-child(4) {
		text-align: right;
	}
</style>
