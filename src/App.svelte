<script>
	let todos = ["learn Svelte", "Create Something"]; // an empty list
	let newTodo = "";

	function handleKeyup(evt){
		if (evt.key == 'Enter'){
			todos = [...todos, newTodo];
			newTodo = "";
		}
		else{
			newTodo = evt.target.value;
		}
	}
</script>

<label>
	New To-Do
	<input type="text" value={newTodo} on:keyup={handleKeyup} />
</label>

{#if todos.length == 0}
	<p>What do you want to work on?</p>
{:else}
	<ul>
		{#each todos as todo}
			<li>{todo}</li>
		{/each}
	</ul>
{/if}
