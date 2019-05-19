<script>
    import TodoItem from './TodoItem.svelte';
	import AddTodo from './AddTodo.svelte';
	import { onMount,afterUpdate } from 'svelte';
	export let name;

	let todosData = [];

	onMount(async ()=> {

		let response = await fetch('http://localhost:3000/todos');

		let result = await response.json();
		
		todosData = result;
		
	})

	afterUpdate(async ()=> {

		let response = await fetch('http://localhost:3000/todos');

		let result = await response.json();
		
		todosData = result;
		
	})

</script>

<style>
	h1 {
		color: purple;
	}
	.mtop{
		margin-top : 15px;
	}
</style>

	<AddTodo />
	<div class="ui container mtop">

	<div class="ui middle aligned divided list">
		{#each todosData as todo}
		    
			<TodoItem  title={todo.title} id={todo.id} isCompleted={todo.iscompleted}/>	
		{/each}
	</div>
</div>
	

