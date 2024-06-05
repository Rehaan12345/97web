<script>
    import { onMount } from "svelte";

    let data;

    async function start() {
        try {
            const url = "http://localhost:8000/";
            const res = await fetch(url);
            if (!res.ok) {
                throw new Error("Fetching didn't work");
            }
            const resData = await res.json();
            data = resData["data"];
        } catch (error) {
            console.log("Error retrieving data: ", error);
        }
    }

    onMount(() => { start(); })
</script>

<h1>{data}</h1>