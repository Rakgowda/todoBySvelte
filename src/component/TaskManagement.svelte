<script>
export let tasks;
export let Completedtasks;
let notasksrc="images/notask.svg"
let deleteSrc = "images/trash.svg"
let doneSrc = "images/checked.svg"
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
}

div.header {
  background-color:#ff4646;
  color: white;
  padding: 10px;
  font-size: 40px;
}

div.container {
  padding: 10px;
}
.flexNumber {
    flex: 0 0 33.333333%;
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
</style>

<div class="taskFlex">
    {#if tasks.length == 0}

        <img class="noTaskImg d-flex m-auto" src={notasksrc} alt="" />
        

    {:else}
    <div class="d-flex m-auto flex-wrap  justify-content-center">
        
        {#each tasks as item}
       
        <div class="card">
            <div class="header">
              <h1>{item.item}</h1>
            </div>
          
            <div class="d-flex justify-content-between">
              <div class="d-flex flex-column p-2 justify-content-start text-left">
                <div class="divSpan m-2">Created on : <span class="spandate">{item.date}</span></div>
                <div class="divSpan m-2">Time spent : <span class="spanspand">{item.spend}</span></div>
              </div>
              <div class="d-flex flex-column p-2 text-left">
                <div class="divSpan m-2">Set time : <input type="time" /> </div>
                <div class="d-flex justify-content-around m-2">
                  <img src={deleteSrc} class="action" on:click={deleteCall(item)} alt="" />
                  <img src={doneSrc} class="action" on:click={doneCall(item)}  alt="" />
                </div>
              </div>
            </div>
          </div>
            
        
        {/each}
  
    </div>
    {/if}

    {#if Completedtasks.length != 0}
<hr>
<div class="d-flex m-auto flex-wrap  justify-content-center">
    
    {#each Completedtasks as item}
  
    <div class="card">
        <div class="completed">
          <h1>{item.item}</h1>
        </div>
      
        <div class="d-flex justify-content-between">
          <div class="d-flex flex-column p-2 justify-content-start text-left">
            <div class="divSpan m-2">Created on : <span class="spandate">{item.date}</span></div>
            <div class="divSpan m-2">Time spent : <span class="spanspand">{item.spend}</span></div>
          </div>
          <div class="d-flex flex-column p-2 text-left">
            <div class="divSpan m-2">Set time : <input type="time" /> </div>
            <div class="d-flex justify-content-around m-2">
              <img src={deleteSrc} class="action" on:click={deleteCallCompleted(item)} alt="" />
              <!-- <img src={doneSrc} class="action" alt="" /> -->
            </div>
          </div>
        </div>
      </div>
        
    
    {/each}

</div>
{/if}

</div>