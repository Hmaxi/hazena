<script>
    import { Button, Willow, Field, Text } from "wx-svelte-core";
    import Match from "../components/match.svelte"
    let name = $state('')
    let start = $state(false)

    function formSubmited(e) {
        e.preventDefault()
        if (name.length > 0)
            start = true
    }

</script>

<Willow>
    <main>
        <h1>Hazena - zapas</h1>
        {#if !start}
            <form onsubmit={formSubmited}>
                <Field label='Souper:' position='left'><Text type='text' id='name' bind:value={name} /></Field>
                <Button type={"primary"}>Start Match</Button>
            </form>
        {:else}
            <Match {name}/> 
        {/if}
    </main>
</Willow>

<style>
    main {
        margin: 1rem auto;
        max-width: 800px;
    }
</style>