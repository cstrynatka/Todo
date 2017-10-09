<template>
	<div class='ui centered card'>
		<div class='content'>
			<div class='header'>
				{{ todo.title }}
			</div>
			<dir class='meta'>
				{{ todo.project }}
			</dir>
			<div class='extra content'>
				<span class='right floated edit icon' v-on:click="showForm">
					<i class='edit icon'></i>
				</span>
				<span class='right floated trash icon' v-on:click="deleteTodo(todo)">
					<i class='trash icon'></i>
				</span>
			</div>
		</div>
		<dir class="content" v-show="isEditing">
			<div class='ui form'>
				<div class='field'>
					<label>Title</label>
					<input type='text' v-model="todo.title">
				</div>
				<div class='field'>
					<label>Project</label>
					<input type='text' v-model="todo.Project">
				</div>
				<div class='ui two button attached buttons'>
					<button class='ui basic blue button' v-on:click="hideForm">
						Close X
					</button>
				</div>
			</div>
		</dir>
		<dir class='ui bottom attached green basic button' v-show="!isEditing && todo.done" disabled>
			Completed
		</dir>
		<div class='ui bottom attached red basic button' v-on:click="completedTodo(todo)" v-show="!isEditing && !todo.done">
			Pending
		</div>
	</div>
</template>

<script type="text/javascript">
	export default {
		props: ['todo'],
		data () {
			return {
				isEditing: false
			}
		},
		methods: {
			completeTodo(todo) {
				this.$emit('complete-todo', todo)
			},
			deleteTodo(todo) {
				this.$emit('delete-todo', todo)
			},
			showForm() {
				this.isEditing = true;
			},
			hideForm() {
				this.isEditing = false;
			}
		}
	}
	</script>