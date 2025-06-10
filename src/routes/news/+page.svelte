<script>
    import { onMount } from "svelte"
    const API_KEY = "3b191e09eacf45dd8844b6e44c31f400"
    const categories = ["business", "entertainment", "general", "health", "science", "sports", "technology"]
    let data = []
    let news = []
    let topheadline = []
    let countrynews = []
    let response
    let category = ""
    let totalresults = 0
    let bitcoinnews = {}
    let allnews = {}
    let newscategory = {}
    let pagesize = 10
    let currentpage = 1
    let loading = false;
    // async function getbitcoinnews(){
    //     response = await fetch(`https://newsapi.org/v2/top-headlines?q=bitcoin&apiKey=${API_KEY}`)
    //     bitcoinnews = await response.json()
    //     console.log(bitcoinnews)
    // }
    // async function getallnews(){
    //     response = await fetch(`https://newsapi.org/v2/top-headlines?q=indonesia&apiKey=${API_KEY}`)
    //     allnews = await response.json()
    //     console.log(allnews)
    // }
    async function getnewscategory(category){
        response = await fetch(`https://newsapi.org/v2/top-headlines?q=${category}&apiKey=${API_KEY}`)
        newscategory = await response.json()
        console.log(newscategory)
    }
    async function loadmorenews(category){
        loading = true
        currentpage++
        const response = await fetch(`https://newsapi.org/v2/top-headlines?q=${category}&pageSize=${pagesize}&page=${currentpage}&apiKey=${API_KEY}`)
        const morenews = await response.json()
        newscategory[category].articles = [...newscategory[category].articles, ...morenews, articles]
        loading = false
    }
    onMount(async()=>{
        // getbitcoinnews()
        // getallnews()
        getnewscategory()
        // categories.forEach(category => getnewscategory(category, pagesize))
        // loadmorenews()
    })
</script>
<div class="container-fluid mt-4">
    <div class="row mb-4">
        <div class="col-lg-12 col-md-12 text-left">
            <!-- {#if bitcoinnews.totalResults > 0}
                <h5>Total bitcoin news : {bitcoinnews.totalResults}</h5>
                {#each bitcoinnews.articles as article}
                    <h2>{article.title}</h2>
                    <p>{article.author}</p>
                    <p>{article.content}</p>
                    <p>{article.description}</p>
                    <a href="{article.url}">{article.url}</a>
                {/each}
            {:else}
            <p>Bitcoin news does not exist</p>
            {/if} -->
            <!-- {#if allnews.totalResults > 0}
                <h5>Total news : {allnews.totalResults}</h5>
                {#each allnews.articles as article}
                    <h2>{article.title}</h2>
                    <p>{article.author}</p>
                    <p>{article.content}</p>
                    <p>{article.description}</p>
                    <a href="{article.url}">{article.url}</a>
                {/each}
            {:else}
                <p>Bitcoin news does not exist</p>
            {/if} -->
            {#each categories as category}
                <button type="button" class="btn btn-success me-2 fw-bold" on:click={()=>getnewscategory(category)}>#{category}</button>
            {/each}
            <h5>Total news : {newscategory.totalResults}</h5>
            {#each newscategory.articles as article}
                <h2>{article.title}</h2>
                <p>{article.author}</p>
                <p>{article.content}</p>
                <p>{article.description}</p>
                <a href="{article.url}">{article.url}</a>
            {/each}
            {#each categories as category}
            <!-- {#if newscategory[category] && newscategory[category.totalResults] > 0}
                <h5>Total news: {newscategory.totalResults}</h5>
                {#each newscategory[category].articles as article}
                    <h2>{article.title}</h2>
                    <p>{article.author}</p>
                    <p>{article.content}</p>
                    <p>{article.description}</p>
                    <a href="{article.url}">{article.url}</a>
                {/each}
            {#if newscategory[category].totalResults > newscategory[category].articles.length}
                <button class="btn btn-primary mt-3" disabled={loading} on:click={() => }></button>
            {/if} -->
            {/each}
        </div>
    </div>
</div>