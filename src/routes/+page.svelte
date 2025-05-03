<script>
    import { Button, Willow } from "wx-svelte-core";
    import Match from "../components/match.svelte"

    let start = false
</script>

<Willow>
    <main>
        <h1>Hazena - zapas</h1>
        {#if !start}
            <Button onclick={() => { start = true }} type={"primary"}>Start Match</Button>
        {:else}
            <Match />
        {/if}
    </main>
</Willow>

<style>
    main {
        margin: 1rem auto;
        max-width: 800px;
    }
</style>