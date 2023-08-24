<script>
    import supabase from "$lib/db";
    import { user } from "$lib/index";
    import { redirect } from '@sveltejs/kit'

    let email = "";
    let password = "";
    const signUp = async () => {
        let { data, error } = await supabase.auth.signUp({
            email: email,
            password: password,
        });
        throw redirect('/')
    };


    const logIn = async () => {
        let { data, error } = await supabase.auth.signInWithPassword({
            email: email,
            password: password,
        });
        
       throw redirect('/');
       
  };

</script>
<div class="mx-10 p-2 my-10">
    <label for="email">
    Email:
        <input type="email" bind:value={email} placeholder=" enter email here">
    </label>
    <br><br>
    <label for="password">
        Password:
            <input type="password" bind:value={password} placeholder=" enter password here">
    </label>
    <br><br>
    <button class="bg-red-700 text-xl p-2 rounded-lg " on:click={signUp}>SignUp</button>
    <button class="bg-red-700 text-xl p-2 rounded-lg " on:click={logIn}>LogIn</button>
</div>
