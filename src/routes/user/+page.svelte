<script>
    import {onMount} from 'svelte'
    let user = []
    onMount(async()=>{
        const fetchUser = await fetch('json/user.json')
        user = await fetchUser.json()
    })
</script>
<div class="container mt-4">
    <h1>About author page</h1>
    <div class="card" style="width: 18rem;">
  <img src="{user.profile_url}" class="card-img-top" alt="...">
  <div class="card-body">
    <h5 class="card-title">{user.username}</h5>
    <p class="card-text">{user.content}</p>
    <a href="/" class="btn btn-primary">Go somewhere</a>
  </div>
</div>
</div>