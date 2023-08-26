<script>
    import supabase from "$lib/db";

    const logout = () => {
        console.log("logout")
        supabase.auth.signOut();
    }
</script>
<div class="my-15 text-center justify-center p-2">
<button on:click={logout} class="bg-red-700 text-xl p-2 rounded-lg">LogOut</button>
</div>

