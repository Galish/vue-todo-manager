<template>
	<div>
		<h3>Todos</h3>

		<div class="todos">
			<div
				class="todo"
				v-for="todo in allTodos"
				:key="todo.id"
				@dblclick="onDblClick(todo)"
				v-bind:class="{ 'is-complete': todo.completed }"
			>
				{{todo.title}}

				<i
					class="delete"
					@click="deleteTodo(todo.id)"
				>
					x
				</i>
			</div>
		</div>
	</div>
</template>

<script>
	import { mapActions, mapGetters } from 'vuex'

	export default {
		name: 'Todos',
		computed: mapGetters([ 'allTodos' ]),
		methods: {
			...mapActions([ 'fetchTodos', 'deleteTodo', 'updateTodo' ]),
			onDblClick({ completed, id, title }) {
				const updatedTodo = {
					id,
					title,
					completed: !completed
				}

				this.updateTodo(updatedTodo)
			}
		},
		created() {
			this.fetchTodos()
		}
	}
</script>

<style scoped>
	.todos {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		grid-gap: 1rem;
	}

	.todo {
		border: 1px solid #ccc;
		background: #41b883;
		padding: 1rem;
		border-radius: 5px;
		text-align: center;
		position: relative;
		cursor: pointer;
	}

	.is-complete {
		background-color: #35495e;
		color: #fff;
	}

	.delete {
		font-style: normal;
		position: absolute;
		right: 10px;
		bottom: 5px;
	}
</style>
