<script>
    import { onMount } from "svelte";
    import supabase from "$lib/db";
    import { user } from "$lib/stores";

    user.set(supabase.auth.user());
        supabase.auth.onAuthStateChange((_, session) => {
        user.set(session?.user)
    })

    let editors = [];
    let showEditor = false;
    let newNote = '';


   
   onMount(async () => {
       let { data, error } = await supabase.from('editors').select('*')
       editors = data;
   })
   console.log(`its the user id ${$user.id}`)
 

   function handleClick(){
    showEditor = true;
   }

   const deleteEditor = async (editor) => {
    const { error } = await supabase
  .from('editors')
  .delete()
  .eq("id", editor.id)
  location.reload();
   }
   
   const insertEditor = async (editors) => {
    try {
        const { data, error} = await supabase  
  .from('editors')
  .insert([{ note: newNote, user_id: $user.id},])
  .select()
  newNote = '';
  location.reload();
    } catch (error) {
        console.log(error)
    }
   }
   
    
   const updateEditor = async (editor) => {
    try {
        const { data, error } = await supabase
            .from('editors')
            .update({ note: editor.note })
            .eq('id', editor.id)
            .select('user_id');
    } catch (error) {
        console.log(error);
    }
}

</script>
<div class="my-15 text-center justify-center p-2">
    <button class="bg-red-700 text-xl p-2 rounded-lg " on:click={handleClick}>click here to see the table</button>
</div>

<div>
    <button class="bg-red-700 text-2xl text-gray-400 p-2 rounded-lg m-2" on:click={() => insertEditor(editors)}>  Add a note </button>
</div>
 


{#each editors as editor}
<div>
    
    <input type="text" class = 'mb-2 border border-gray-200 mx-10'value={editor.note} on:input={(e) => {
        editor.note = e.currentTarget.value;

    }}>
    <button class="bg-red-700 text-xl p-1 rounded-lg m-2 text-gray-400" on:click={() => deleteEditor(editor)}>Delete</button>
    <br>
    <button class="bg-red-700 text-xl p-1 rounded-lg m-2" on:click={() => updateEditor(editor)}> submit</button>
</div>
{:else}
 <p>No editors found</p>
{/each}