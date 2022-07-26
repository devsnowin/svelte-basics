<script>
	import TodoForm from "./components/TodoForm.svelte";

	let todos = localStorage.getItem("todos")
		? JSON.parse(localStorage.getItem("todos"))
		: [];

	function addTodo(todo) {
		if (todo !== "") {
			todos.push({
				title: todo,
				done: false,
			});
		}
		todos = todos;
	}

	function removeTodo(index) {
		todos.splice(index, 1);
		todos = todos;
	}

	$: localStorage.setItem("todos", JSON.stringify(todos));
</script>

<main>
	<TodoForm {addTodo} />
	<ul>
		{#each todos as { title, done }, index}
			<li class="todo-con">
				<p class:done on:click={() => (done = !done)}>{title}</p>
				{#if done} <span>✔</span> {/if}
				<span class="delete" on:click={() => removeTodo(index)}>❌</span
				>
			</li>
		{/each}
	</ul>
</main>

<style>
	:global(*) {
		margin: 0 !important;
		padding: 0 !important;
		box-sizing: border-box !important;
	}

	main {
		max-width: 60rem;
		min-height: 100vh;
		margin: 0 auto !important;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 4rem;
		text-align: center;
	}

	.todo-con {
		text-align: left !important;
		cursor: pointer;
		display: flex;
		align-items: center;
		gap: 1rem;
	}

	.todo-con span {
		text-decoration: none !important;
		color: green;
	}

	.done {
		text-decoration: line-through;
	}

	.delete:hover {
		transition: all 0.2s ease-in-out;
		transform: scale(1.2);
	}
</style>
