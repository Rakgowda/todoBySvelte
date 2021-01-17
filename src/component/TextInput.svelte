<script>
export let task;
import { createEventDispatcher } from 'svelte';

const dispatch = createEventDispatcher();

function rak(e) {

    if(e.key == "Enter")
    {
        console.log("hello")
        console.log(task)
        dispatch('taskValue',task);
        e.target.value = "";
    }
}
</script>

<style>
.textadd{
    background-color: transparent;
    border: 2px solid black;
    width:50rem;
    text-transform: uppercase;
    font-weight: bold;
}

.textadd::placeholder{
    text-align: center;
    text-transform: uppercase;
}

</style>

<div class="divCenter">
    <input class="d-flex m-auto textadd" type="text" placeholder="Enter Task" bind:value={task} on:keypress={rak}/>
</div>