<script>
    import supabase from "$lib/db";
    import { goto } from "$app/navigation";
    let email = "";
    let password = "";
    const signUp = async () => {
        let { data, error } = await supabase.auth.signUp({
            email: email,
            password: password,
        });
        goto("/");
    };

    const signIn = async () => {
        let { data, error } = await supabase.auth.signIn({
            email: email,
            password: password,
        });
        goto("/");
    };
</script>

<div class="mx-10 p-2 my-10">
    <label for="email">
        Email<span class="text-red-700 text-sm">* </span>
        <input
            type="email"
            bind:value={email}
            placeholder=" enter email here"
            class="mb-2 border border-gray-200"
        />
    </label>
    <br /><br />
    <label for="password">
        Password<span class="text-red-700 text-sm">* </span>:
        <input
            type="password"
            bind:value={password}
            placeholder=" enter password here"
            class="mb-2 border border-gray-200"
        />
    </label><br /><br />
    {#if password.length < 8}
        password must be 8 characters long
    {/if}
    <br /><br />
    <button class="bg-red-700 text-xl p-1 rounded-lg" on:click={signUp}
        >SignUp</button
    >
    <button class="bg-red-700 text-xl p-1 rounded-lg" on:click={signIn}
        >LogIn</button
    >
</div>
