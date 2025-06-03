<script>
    const API_KEY = "3b191e09eacf45dd8844b6e44c31f400"
    const BASE_URL = "https://newsapi.org/v2/everything"
    let news = []
    async function getAllNews() {
        response = await fetch (`${BASE_URL}&apikey=${API_KEY}`)
        news = await response.json()
        console.log(news);
    }
    onMount(async()=>{
        getAllNews()
    })
</script>

