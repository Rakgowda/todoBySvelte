<script>
	import Header from "./component/Header.svelte";
	import AddTaskText from "./component/TextInput.svelte"
	import TaskManagement from "./component/TaskManagement.svelte"
	let tasks=[]
	function taskHandler(e)
	{
		console.log("from app "+e.detail)
		tasks = [...tasks,e.detail]
		console.log(tasks)
	}
</script>

<Header></Header>



<AddTaskText on:taskValue={taskHandler}>

</AddTaskText>

<TaskManagement {tasks}>

</TaskManagement>

<main>
	<!-- <h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p> -->
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