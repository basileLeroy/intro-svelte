<script>
	import { todos } from './store'
	import Todos from './Todos.svelte';
	import { v4 as uuidv4 } from 'uuid';
	export let user;
	
	let value = "";
	let completed = false

	function addTodo() {
		let id = uuidv4();
		$todos = [...$todos, { value, completed, id}];

		value = null;
	}

	function filteredList() {
        $todos = $todos.filter(todo => todo.completed === false);
    }
	
</script>

<main>
	<div class="position-absolute top-50 start-50 translate-middle container-sm p-3 mb-2 bg-info text-dark rounded">
		<h1>{user}'s TODO list</h1>
		<div class="input-group mb-3">
			<input type="text" placeholder="New Todo ..." bind:value/>
			<button class="btn btn-primary" on:click={ addTodo }>Add</button>
			<button class="btn btn-warning" on:click={ filteredList }>Clear Completed todo's</button>
		</div>
		
		<Todos/>
	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
