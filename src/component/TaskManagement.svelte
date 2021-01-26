<script>
export let tasks;
export let Completedtasks;
let playClick = false;
let notasksrc="images/notask.svg"
let deleteSrc = "images/trash.svg"
let doneSrc = "images/checked.svg"
let thumbs = "images/thumbs-up.svg"
let play = "images/play.svg"
let pause = "images/pause.svg"

import { createEventDispatcher } from 'svelte';

const dispatch = createEventDispatcher();

function deleteCall(e){
// console.log(e)
dispatch("deleteTask",e);
}
function doneCall(e){
// console.log(e)
dispatch("doneCall",e);
}
function deleteCallCompleted(e){
// console.log(e)
dispatch("deleteCallCompleted",e);
}

function changePlayClickState(i) { 
  debugger
  console.log(tasks[i].play)
  
  if(tasks[i].play)
  {
    tasks[i].play=false;
  }
  else{
    tasks[i].play=true;
  }
 }


</script>
<style>
.noTaskImg{
    width: 30rem;
    height: 30rem;
}
.taskFlex{
    /* display: flex; */
    margin-top: 30px;
}
div.card {
  width: 250px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  text-align: center;
  margin: 5px;
  border: transparent;
  flex: 0 0 33.333333%;
  padding: 20px;
}

.incompleteTask {
  background-color:#4a9bf1;
  /* color: ; */

}
.completeTask {
  background-color:#0cec7c;
  /* color: ; */

}
.itemText {
 font-size: 20px;
font-weight: bold;
}
.cc {
  transform: translateX(25%);
}


.action{
  width: 20px;
  height: 20px;
}

.card{
  min-width: 600px;
  
}

.playpause{
  margin-top: auto;
margin-bottom: auto;
}


</style>

<div class="taskFlex">
    {#if tasks.length == 0}

        <img class="noTaskImg d-flex m-auto" src={notasksrc} alt="" />
        

    {:else}
    <div class="d-flex flex-column cc">
        
        {#each tasks as item,i}
       <div class="d-flex">
        <div class="card incompleteTask">
          <div class="row">

          <div class="col-md-2 m-auto">
            <img src={doneSrc} class="action" on:click={doneCall(item)}  alt="" /></div>
          <div class="col-md-8 align-self-center">
            <div class="itemText text-uppercase">
            {item.item}
            </div>
          </div>
          <div class="col-md-2 m-auto"> <img src={deleteSrc} class="action" on:click={deleteCall(item)} alt="" /></div>
          
          </div>
  
          </div>
         <div class="playpause">
           {#if !item.play}
          <img src={play} class="action" on:click={()=>changePlayClickState(i)} alt="" />
          {:else}
          <img src={pause} class="action" on:click={()=>changePlayClickState(i)} alt="" />
          {/if}
         </div>

        </div>
            
        
        {/each}
  
    </div>
    {/if}

    {#if Completedtasks.length != 0}
<hr>
<div class="d-flex m-auto flex-column cc">
    
    {#each Completedtasks as item}
  
    <div class="card completeTask">
      <div class="row">

      <div class="col-md-2 m-auto">
        <img src={thumbs} class="action"  data-toggle="modal" data-target="#myModal"  alt="" />
      </div>
      <div class="col-md-8 align-self-center">
        <div class="itemText text-uppercase">
        {item.item}
        </div>
      </div>
      <div class="col-md-2 m-auto"> <img src={deleteSrc} class="action" on:click={deleteCallCompleted()} alt="" /></div>
      
      </div>

      </div>
        
    
    {/each}

</div>
{/if}

 <!-- The Modal -->
 <div class="modal fade" id="myModal">
  <div class="modal-dialog modal-dialog-centered modal-sm">
    <div class="modal-content">
   
      <!-- Modal body -->
      <div class="modal-body text-center">
        You have done it boss
      </div>
      
      <!-- Modal footer -->
      <div class="modal-footer">
        <button type="button" class="btn btn-primary" data-dismiss="modal">Done</button>
      </div>
      
    </div>
  </div>
</div>

</div>