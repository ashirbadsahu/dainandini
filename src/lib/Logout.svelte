<script>
    import supabase from "$lib/db";
    import { goto } from "$app/navigation"

    const logout = async () => { {
       await supabase.auth.signOut();
    }
    goto('/login')
    }
</script>



<div class="my-15 text-center justify-center p-2">
<button on:click={logout} class="text-2xl text-zinc-400 hover:underline px-2 py-0 hover:border-white border-2 rounded-md bg-transparent">LogOut</button>
</div>
