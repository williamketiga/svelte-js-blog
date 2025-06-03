<script>
    import 'bootstrap/dist/css/bootstrap.min.css'
    import { onMount } from 'svelte';
    onMount(async()=>{
        await import('bootstrap/dist/js/bootstrap.bundle.min.js')
    })
</script>
<nav class="navbar navbar-expand-lg bg-body-tertiary text-white" data-bs-theme="dark">
  <div class="container-fluid">
    <a class="navbar-brand" href="/">Svelte</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse me-auto" id="navbarSupportedContent">
      <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <a class="nav-link active" aria-current="page" href="/">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" aria-disabled="true" href="/admin">Blog</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" aria-disabled="true" href="/user">User</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" aria-disabled="true" href="/news">News</a>
        </li>
      </ul>
    </div>
  </div>
</nav>
<main class="container mt-4">
    <slot/>
</main>
<footer class="text-center bg-body-tertiary text-white fixed-bottom" data-bs-theme="dark">
  <div class="text-center p-3" style="background-color: rgba(0, 0, 0, 0.05);">
    © 2020 Copyright: Kodingnext.com
  </div>
</footer>