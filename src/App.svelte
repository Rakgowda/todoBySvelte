<script>
	import Header from "./component/Header.svelte";
	import AddTaskText from "./component/TextInput.svelte"
	import TaskManagement from "./component/TaskManagement.svelte"
	import moment from 'moment';

	let tasks=[]
	let Completedtasks=[]

	let localtask = window.localStorage.getItem("tasks");
	let localCompltedtask = window.localStorage.getItem("completedtask")
// console.log(JSON.parse(localtask))
if(localtask != null )
{
	tasks= JSON.parse(localtask)
}

if(localCompltedtask != null)
{
	Completedtasks = JSON.parse(localCompltedtask)
}

	function taskHandler(e)
	{
		console.log("from app "+e.detail)
		let task = {}
		task["item"] = e.detail;
		task["date"] = moment().format("DD-MM-YYYY");
		task["spend"] = 0;

		tasks = [...tasks,task]
		window.localStorage.setItem("tasks",JSON.stringify(tasks))
		console.log(JSON.stringify(tasks))
		// console.log()

	}

	function deleteTask(e) { 
		console.log(e.detail)
		let item = e.detail;

		let newTask = tasks.filter(e=> e.item !== item.item);
		
		tasks=newTask;
		window.localStorage.setItem("tasks",JSON.stringify(tasks))
	 }
	 function doneCall(e) { 
		console.log(e.detail)
		let item = e.detail;

		let newTask = tasks.filter(e=> e.item !== item.item);
		console.log(newTask)
		Completedtasks = [...Completedtasks,item]
		tasks=newTask;
		window.localStorage.setItem("tasks",JSON.stringify(tasks))
		window.localStorage.setItem("completedtask",JSON.stringify(Completedtasks))
	 }
	 function deleteCallCompleted(e) {
		console.log(e.detail)
		let item = e.detail;

		let newTask = Completedtasks.filter(e=> e.item !== item.item);
		
		Completedtasks=newTask;
		window.localStorage.setItem("completedtask",JSON.stringify(Completedtasks))

	   }
</script>

<Header></Header>



<AddTaskText on:taskValue={taskHandler}>

</AddTaskText>

<TaskManagement {tasks} {Completedtasks} on:deleteCallCompleted={deleteCallCompleted} on:deleteTask={deleteTask} on:doneCall={doneCall}>

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