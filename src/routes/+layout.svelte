<script>
    import "../app.css";
    import { dev } from '$app/environment';
    import { inject } from '@vercel/analytics';
    inject({ mode: dev ? 'development' : 'production' });
  </script>
  <slot />
  <div class="flex justify-center text-center">
    <footer class="text-lg text-white">Made with ❤️ by Ashish</footer>
  </div>

<!-- Font Oswald -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
  href="https://fonts.googleapis.com/css2?family=Oswald:wght@600&display=swap"
  rel="stylesheet"
/>
<!-- Font open sans -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
  href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@300&display=swap"
  rel="stylesheet"
/>
<!-- Font pacifico -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
  href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap"
  rel="stylesheet"
/>

<style lang="postcss">
  :global(html) {
    background-color: theme(colors.stone.950);
    margin-left: 2rem;
    margin-right: 2rem;
  }
</style>
