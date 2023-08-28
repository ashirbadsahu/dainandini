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
<button on:click={logout} class="bg-red-700 text-xl p-2 rounded-lg">LogOut</button>
</div>
