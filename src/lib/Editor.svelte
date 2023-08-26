<script>
    import { onMount } from "svelte";
    import supabase from "$lib/db";
    let editors = [];
    let showEditor = false;
   
   onMount(async () => {
       let { data, error } = await supabase.from('editors').select('*')
       editors = data;
    //    console.table(editors)
   })
 

   function handleClick(){
    showEditor = true;
   }
   
let updateEditor;
  updateEditor = async (editor) => {
    try {
        const { data, error, user_id } = await supabase
  .from('editors')
  .update({ note: editor.note, user_id})
  .eq('id', editor.id)
  .select()
    } catch (error) {
       console.log(error) 
    }
   }

</script>
<div class="my-15 text-center justify-center p-2">
    <button class="bg-red-700 text-xl p-2 rounded-lg " on:click={handleClick}>click here to see the table</button>
</div>


{#if showEditor }
{#each editors as editor}
<div>
    <input type="text" class = 'border-red-100 mx-10 p-1 border-r-2 outline-1'value={editor.note} on:input={(e) => {
        editor.note = e.currentTarget.value;

    }}>
    <br>
    <button class="bg-red-700 text-xl p-1 rounded-lg m-2" on:click={updateEditor(editor)}> submit</button>
</div>
{:else}
 <p>No editors found</p>
{/each}
{/if}