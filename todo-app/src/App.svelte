<script>
	let newItem = ''
	let todoList = []

	// TODO: prevent to take spaces as imput because you shouldnt store emptiness
	// TODO: prevent accepting blank input when modifying current items
	
	function addItem() {
		if (newItem === '' || newItem === undefined) return;
		todoList = [...todoList, newItem]
		newItem = ''
	}

	function delItem(index) {
		todoList.splice(index, 1)
		todoList = todoList
	}

	function modItem(index, value) {
		todoList.splice(index, 1, value)
		todoList = [...todoList]
	}

</script>

<main class="container">
	<article class="todo-list">

		<h1>TO-DO LIST</h1>

		<article class="list-item">
			<input type="text" bind:value={newItem} maxlength="38" placeholder="Write your task here">
			<span class="btn" on:click={addItem}>💾</span>
		</article>

		{#each todoList as item, index}
		<article class="list-item">
			<input type="text" bind:value={item} on:blur={() => modItem(index, item)} maxlength="38">
			<span class="btn" on:click={() => delItem(index)}>✔</span>
		</article>
		{/each}

	</article>
</main>

<style>
	.container {
		width: 1000px;
		margin-right: auto;
		margin-left: auto;
		display: flex;
		justify-content: center;
	}

	.todo-list {
		width: 500px;
		height: 300px;
	}

	h1 {
		text-align: center;
		margin: 15px;
		font-size: 36pt;
		font-weight: lighter;
		user-select: none;
	}

	input:focus {
		border: 1px solid #e2e2e2;
		border-radius: 5px;
	}

	input {
		padding: 5px 10px;
		width: 100%;
		border: none;
		outline: none;
		font-size: larger;
	}

    .list-item {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-items: center;
		justify-content: space-between;
		padding: 5px;
		margin-bottom: 15px;
		border-radius: 5px;
		box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px, rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
	}

	.btn {
		width: 35px;
		height: 35px;
		padding: 5px;
		margin-left: 10px;
		text-align: center;
		border-radius: 5px;
		border: 1px solid #e2e2e2;
		user-select: none;
	}

	.btn:hover {
		background: #e2e2e2;
	}

	@media screen and (max-width: 1000px) {
		.container {
			margin-right: 0;
			margin-left: 0;
			width: 100%;
		}
	}
</style>