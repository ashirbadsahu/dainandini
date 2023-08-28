<script>
    import { onMount } from "svelte";
    import supabase from "$lib/db";
    import { user } from "$lib/stores";
    import Logout from "./Logout.svelte";

    user.set(supabase.auth.user());
        supabase.auth.onAuthStateChange((_, session) => {
        user.set(session?.user)
    })

    let editors = [];
    let newNote = '';


   
   onMount(async () => {
       let { data, error } = await supabase.from('editors').select('*')
       editors = data;
   })

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
 <!-- Navbar -->
 <div>
    <nav>
        <div class="flex flex-wrap justify-between items-center mx-auto max-w-screen-xl p-4">
            <a href="/" class="flex items-center">
                <img src="https://svgshare.com/i/wzs.svg" class="h-12 mr-3" alt="Dainandini Logo" />
            </a>
            <div class="flex items-center">
                <Logout />
            </div>
        </div>
    </nav>

</div>

<div class="m-4 p-4">
    <button class="text-2xl text-zinc-400 hover:underline px-2 py-0 border-white border-2 rounded-md bg-transparent" on:click={() => insertEditor(editors)}>  Add a note </button>
</div>
 


{#each editors as editor}
<div class="mx-8 space-y-4">
    <div>
    <textarea id="noteBox" rows="15" class="block p-2.5 w-2/3 text-sm text-white bg-transparent rounded-lg border border-white" placeholder="Write your notes here..." on:input={(e) => {
        editor.note = e.currentTarget.value;

    }}></textarea>
</div>
    <div class="flex flex-row justify-between w-2/3">
        <div class="w-36 h-12 relative">
        <div class="w-24 h-8 left-[3px] top-[4px] absolute bg-white rounded-lg"></div>
         <button class="w-24 h-8 left-0 top-[1px] absolute bg-zinc-500 rounded-lg border-2 border-white text-white text-xl font-semibold font-['Oswald'] hover:bg-zinc-600" on:click={() => updateEditor(editor)}>Save</button>   
        </div>
    <button class="text-xl text my-[-2rem] text-zinc-400 hover:underline hover:border-white border- rounded-md bg-transparent" on:click={() => deleteEditor(editor)}>Delete</button>
    </div>  

</div>
{:else}
 <p>No editors found</p>
{/each}

