<script>
    import Editor from "../lib/Editor.svelte";
    import { user } from "$lib/stores";
    import supabase from "$lib/db";
    user.set(supabase.auth.user());
    console.log(supabase.auth.user())
    
    supabase.auth.onAuthStateChange((_, session) => {
        user.set(session?.user)
    })
</script>
<Editor />

    <h4>Welcome {$user.email}</h4>
