<script>
	import {fade} from 'svelte/transition';
	let books = ["Learning Svelte", "The Zen of Cooking Tea"];
	let newBook = "";

	function addBook(evt) {
		if (evt.key == "Enter" && newBook != "") {
			books = [...books, newBook];
			newBook = "";
		}
	}
</script>

<main>
	<h1>My Little Book App</h1>
	<h2>Add Book</h2>
	<input type="text" bind:value={newBook} on:keydown={addBook} />
	<h2>My Books</h2>
	{#each books as book}
		<li transition:fade>{book}</li>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: white;
		font-size: 3em;
		font-weight: 100;
		background: teal;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	main {
		background-image: linear-gradient(teal, white);
	}

	input {
		padding: 5px 10px;
	}
	li {
		list-style:none;
	}
</style>
