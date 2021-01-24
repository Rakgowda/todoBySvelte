<script>
export let tasks;
export let Completedtasks;
let notasksrc="images/notask.svg"
let deleteSrc = "images/trash.svg"
let doneSrc = "images/checked.svg"
let thumbs = "images/thumbs-up.svg"

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
.divSpan{
  font-size: .7rem;
}
.spandate{
  color: green;
  font-size: 1rem;
  font-weight: bold;

}
.spanspand{
  color: tomato;
  font-size: 1rem;
  font-weight: bold;


}

.action{
  width: 20px;
  height: 20px;
}
.completed{
  background-color: #00af91;
  color: white;
  padding: 10px;
  font-size: 40px;
}
.card{
  min-width: 600px;
  
}


</style>

<div class="taskFlex">
    {#if tasks.length == 0}

        <img class="noTaskImg d-flex m-auto" src={notasksrc} alt="" />
        

    {:else}
    <div class="d-flex flex-column cc">
        
        {#each tasks as item}
       
        <div class="card incompleteTask">
          <div class="row">

          <div class="col-md-2 m-auto">
            <img src={doneSrc} class="action" on:click={doneCall(item)}  alt="" /></div>
          <div class="col-md-8 align-self-center">
            <div class="itemText">
            {item.item}
            </div>
          </div>
          <div class="col-md-2 m-auto"> <img src={deleteSrc} class="action" on:click={deleteCall(item)} alt="" /></div>
          
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
        <div class="itemText">
        {item.item}
        </div>
      </div>
      <div class="col-md-2 m-auto"> <img src={deleteSrc} class="action" on:click={deleteCallCompleted(item)} alt="" /></div>
      
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