<script>
  import { onMount } from "svelte";
  import Editor from "../lib/Editor.svelte";
  import { user } from "$lib/stores";
  import supabase from "$lib/db";
  import Components from "../lib/components.svelte";

  let isLoggedIn = false;

  const updateUserStatus = (session) => {
    if (session?.user) {
      user.set(session.user);
      isLoggedIn = true;
    } else {
      user.set(null);
      isLoggedIn = false;
    }
  };

  onMount(() => {
    const session = supabase.auth.session();
    updateUserStatus(session);

    supabase.auth.onAuthStateChange((_, session) => {
      updateUserStatus(session);
    });
  });
</script>

{#if isLoggedIn}
  <Editor />
{:else}
  <Components />
{/if}
