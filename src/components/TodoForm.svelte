<script>
    export let addTodo;
    let newTodo;

    function handleSubmit() {
        addTodo(newTodo);
        newTodo = "";
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <label for="todo">New Todo</label>
    <input
        bind:value={newTodo}
        class="todo-input"
        type="text"
        placeholder=" Eg: keep learning..."
    />
    <input type="submit" />
</form>

<style>
    form {
        width: 30rem;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: flex-start;
        gap: 1rem;
    }

    label {
        text-align: left;
        font-weight: bold;
    }

    .todo-input {
        padding-inline: 1rem !important;
    }
</style>
