<script>
   export let id;
   export let title;
   export let isCompleted;

   async function handleClick(id,title){

       let data = {
           id : id,
           title : title,
           iscompleted : true
       }
       let response = await fetch(`http://localhost:3000/todos/${id}`,{
           method : 'PUT',
           headers : {
               'content-type' : 'application/json'
           },
           body : JSON.stringify(data) 
       });

       let result = await response.json();
       console.log(result);
   }
</script>

<style>
    .completed{
        background : green;
    }
</style>

<div class="item">
{#if isCompleted }

    <div class="content completed">
            {title}
    </div>
{:else }
    <div class="right floated content">
        <div class="ui button" on:click={() => handleClick(id,title)}>Mark as completed</div>
    </div>

    <div class="content">
        {title}
    </div>
{/if}			   
</div>