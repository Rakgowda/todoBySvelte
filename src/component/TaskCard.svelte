<script>

</script>

<style>

</style>
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
       {#if !playClick}
      <img src={play} class="action" on:click={()=>changePlayClickState()} alt="" />
      {:else}
      <img src={pause} class="action" on:click={()=>changePlayClickState()} alt="" />
      {/if}
     </div>

    </div>
        