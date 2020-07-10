<template>
	<div>
		Filter Todos:

		<select @change="filterTodos($event)">
			<option vlaue="200">200</option>
			<option vlaue="100">100</option>
			<option vlaue="50">50</option>
			<option vlaue="20">20</option>
			<option vlaue="10">10</option>
			<option vlaue="5">5</option>
		</select>
	</div>
</template>

<script>
	import { mapActions } from 'vuex'

	export default {
		name: 'FilterTodos',
		methods: mapActions([ 'filterTodos' ])
	}
</script>

<style>
	select {
		margin-top: 20px;
		padding: 6px;
		border: 1px solid #41b883;
		outline: none;
	}
</style>
