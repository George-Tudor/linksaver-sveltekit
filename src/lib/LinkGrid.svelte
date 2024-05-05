<script>

    import LinkItem from "./LinkItem.svelte";
    import {createEventDispatcher} from "svelte";

    export let links;
    const dispatch = createEventDispatcher();
</script>

<section id="links">
    {#each links as link}
        <LinkItem on:delete={event => dispatch("delete", event.detail)} link={link}/>
    {/each}
</section>

<style>
    section {
        width: 100%;
        display: grid;
        grid-template-columns: 1fr;
        grid-gap: 1rem;
    }

    @media (min-width: 768px) {
        section {
            grid-template-columns: repeat(5, 1fr);
        }
    }
</style>
