<script>
  import { goto } from "$app/navigation";

  function handleGetStarted() {
    goto("/login");
  }
</script>

<!-- Navbar -->

<div>
  <nav>
    <div
      class="flex flex-wrap justify-between items-center mx-auto max-w-screen-xl p-4"
    >
      <a href="/" class="flex items-center">
        <img
          src="https://svgshare.com/i/wzs.svg"
          class="h-12 mr-3 max-md:h-10"
          alt="Dainandini Logo"
        />
      </a>
      <div class="flex items-center">
        <a
          href="/login"
          class="text-2xl max-md:text-xl text-zinc-400 hover:underline px-2 py-0 hover:border-white border-2 rounded-md"
          >Login</a
        >
      </div>
    </div>
  </nav>

  <!-- contents -->
</div>
<div class="flex flex-col min-h-screen justify-center items-center my-[-4rem]">
  <!-- Namaste -->
  <div class="hover:text-6xl text-5xl max-md:text-3xl max-md:hover:text-4xl">
    <div>
      <span class="text-zinc-400 font-normal font-['Pacifico']">Namaste</span
      ><span class="text-white font-bold"> 🙏</span>
    </div>
  </div>
  <br />
  <!-- Tagline -->
  <div
    class="text-white text-5xl max-md:text-3xl font-['Oswald'] font-bold relative text-center"
  >
    Capture your thoughts, Anytime, Anywhere
  </div>
  <br />
  <div
    class="text-center w-1/2 text-white text-sm mx-4 font-light font-['Open Sans'] leading-4 max-md:w-3/4"
  >
    Write and edit your notes with a distraction-free interface, access your
    notes from any device, anywhere, Scribble down thoughts, save your moments,
    pen epic tales, and uncover the mysteries of the universe (or just keep
    track of your grocery lists).
  </div>
  <br />

<<<<<<< HEAD
    <!-- GET STARTED button -->
    <div class="w-60 h-16 max-md:w-40 max-md:h-12 relative">
        <div class="w-40 h-12 max-md:w-32 max-md:h-9 left-[3px] top-[4px] absolute bg-white rounded-lg"></div>
        <button class="w-40 h-12 left-0 top-[1px] max-md:w-32 max-md:h-9 absolute bg-zinc-500 rounded-lg border-2 border-white text-white text-2xl font-semibold font-['Oswald'] hover:bg-zinc-600 max-md:text-xl transition hover:scale-110 hover:duration-150 ease-in-out" on:click={() => handleGetStarted()}>GET STARTED</button>
      </div>
=======
  <!-- GET STARTED button -->
  <div class="w-60 h-16 max-md:w-40 max-md:h-12 relative">
    <div
      class="w-40 h-12 max-md:w-32 max-md:h-9 left-[3px] top-[4px] absolute bg-white rounded-lg"
    ></div>
    <button
      class="w-40 h-12 left-0 top-[1px] max-md:w-32 max-md:h-9 absolute bg-zinc-500 rounded-lg border-2 border-white text-white text-2xl font-semibold font-['Oswald'] hover:bg-zinc-600 max-md:text-xl"
      on:click={() => handleGetStarted()}>GET STARTED</button
    >
  </div>
>>>>>>> f9461de180bf1972f3598184edf30c2142ca385c
</div>
<!-- Bottom styled text -->
<div class="flex justify-center my-[-6rem]">
  <div
    class=" mx-6 origin-top-left rotate-[-4.36deg] opacity-20 text-zinc-400 text-md font-normal underline font-['Open Sans'] max-md:text-sm"
  >
    Today was a whirlwind of gears and circuits! My day started with a double
    shot of espresso and a determined mindset to conquer the world of
    engineering. The morning lecture on quantum mechanics left my brain feeling
    both electrified and bewildered – Schrödinger's cat definitely has more than
    nine lives in my mind right now. The highlight of the day was the lab
    session where we dabbled in soldering components onto a PCB.<br /><br />My
    shaky hands turned a simple LED circuit into a modern art masterpiece, but
    hey, it lit up! In the midst of it all, I found a new appreciation for my
    calculator – it's become my sidekick in this battle against complex
    equations. As the sun set, I retreated to my fortress of textbooks and
    online resources, ready to dive into the mysteries of thermodynamics. I'll
    conquer these subjects one equation at a time, just you wait.
  </div>
</div>

<!-- Footer text -->
<div></div>
