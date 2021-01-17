<script>
export let tasks;
let notasksrc="images/notask.svg"
import moment from 'moment';

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
  background-color: #010801;
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
</style>

<div class="taskFlex">
    {#if tasks.length == 0}

        <img class="noTaskImg d-flex m-auto" src={notasksrc} alt="" />
        

    {:else}
    <div class="d-flex m-auto flex-wrap  justify-content-center">
        
        {#each tasks as item}
       
        <div class="card">
            <div class="header">
              <h1>{item}</h1>
            </div>
          
            <div class="container">
              <p>{moment().format("MMMM Do YYYY, h:mm:ss a")}</p>
            </div>
          </div>
            
        
        {/each}
  
    </div>
    {/if}


</div>