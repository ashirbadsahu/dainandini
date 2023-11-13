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

  //key bindings
  const onKeyDown = (e) =>{
    if(e.key === "Enter"){
      signIn();
    }
  }
</script>

<!-- nav bar -->
<div>
  <nav>
    <div
      class="flex flex-wrap justify-between items-center mx-auto max-w-screen-xl p-4"
    >
      <a href="/" class="flex items-center">
        <img
          src="https://svgshare.com/i/wzs.svg"
          class="h-12 mr-3"
          alt="Dainandini Logo"
        />
      </a>
    </div>
  </nav>
</div>
<!-- login inputs -->

<div class="flex flex-col min-h-screen justify-center items-center my-[-6rem]">
  <div class="w-84 h-84 rounded-lg border-2 border-white">
    <div class="mx-10 p-2 my-10">
      <!-- email input filed -->
      <label for="email" class="text-white">
        Email<span class="text-red-700 text-sm">* </span><span>: </span>
        <input
          type="email"
          bind:value={email}
          placeholder=" enter email here"
          class="mb-2 border-b-2 border-gray-200 text-gray-300 bg-transparent outline-none"
       on:keydown={onKeyDown} />
      </label>
      <br /><br />
      <!-- password input field -->
      <label for="password" class="text-white">
        Password<span class="text-red-700 text-sm">* </span>:
        <input
          type="password"
          bind:value={password}
          placeholder=" enter password here"
          class="mb-2 border-b-2 border-gray-200 text-gray-300 bg-transparent outline-none"
       on:keydown={onKeyDown} />
      </label><br /><br />
      {#if password.length < 8}
        <p class="text-white">Password must be 8 characters long</p>
      {/if}
      <br /><br />
      <div class="flex text-center space-x-4 justify-center">
        <button
          class="text-2xl text-zinc-400 hover:underline px-2 py-0 hover:border-white border-2 rounded-md"
          on:click={signUp}>SignUp</button
        >
        <button
          class="text-2xl text-zinc-400 hover:underline px-2 py-0 hover:border-white border-2 rounded-md"
          on:click={signIn}>LogIn</button
        >
      </div>
    </div>
  </div>
</div>