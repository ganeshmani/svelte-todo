<script>
    let titleValue = '';

    async function addTodo(title){

          let data = {
           title : title,
           iscompleted : false
       }
       let response = await fetch(`http://localhost:3000/todos`,{
           method : 'POST',
           headers : {
               'content-type' : 'application/json'
           },
           body : JSON.stringify(data) 
       });
       let result = await response.json();
        
        titleValue = '';
    }

</script>


<style>

</style>


<div class="ui fluid action input">
		<input type="text" bind:value={titleValue} placeholder="Enter todo...">
		<div class="ui button" on:click={() => addTodo(titleValue)}>Add</div>
</div>