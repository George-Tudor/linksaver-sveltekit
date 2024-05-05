<script>
    import {createEventDispatcher} from "svelte";

    export let link;
    const dispatch = createEventDispatcher();

    function formatTags(tags) {
        return tags.map(tag => `#${tag}`);
    }

</script>

<article>
    <button class="close-btn" on:click={() => dispatch("delete", link)}>&times;</button>
    <header>
        <h1>{link.title}</h1>
        <h2>{link.description}</h2>
        <h3><a href="{link.url}"target="_blank">{link.url}</a></h3>
    </header>
    <div class="image">
        <img src="{link.imageUrl}" alt="{link.title} picture">
    </div>
    <div class="content">
        {#if link.userNotes !== undefined && link.userNotes.length > 0}
            <h3>Notes</h3>
            <p>{link.userNotes}</p>
        {/if}
        {#if link.tags !== undefined && link.tags.length > 0}
            <h3>Tags</h3>
            <p class="tags">{formatTags(link.tags).join(' ')}</p>
        {/if}
    </div>
    <footer>
        <button>Add Tag</button>
        <button>Edit Notes</button>
    </footer>
</article>

<style>
    article {
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
        border-radius: 5px;
        background: white;
        margin: 1rem;
        position: relative;
    }

    @media (min-width: 768px) {
        article {
            margin: 0.5rem;
        }
    }

    header,
    .content,
    footer {
        padding: 1rem;
    }

    .content {
        text-align: left;
        padding: 0.5rem;
    }

    .close-btn {
        font-size: 16px;
        color: black;
        background-color: white;
        cursor: pointer;
        padding: 3px 6px;
        border-radius: 2px;
        position: absolute;
        right: 0;
    }


    .image {
        width: 100%;
        height: 10rem;
        margin: 0.25rem 0;
    }

    .image img {
        width: 100%;
        height: 100%;
        object-fit: contain;
        display: block;
    }

    h1 {
        font-size: 1.25rem;
        margin: 0.5rem 0;
        font-family: "Roboto Slab", sans-serif;
        margin: 0.5rem 0;
        padding: 0;
        margin-bottom: 0.25rem;
    }

    h2 {
        font-size: 1rem;
        color: #808080;
        margin: 0.5rem 0;
    }

    h3 {
        margin: 0.5rem 0;
        padding: 0;
    }

    p {
        font-size: 1rem;
        color: #808080;
        margin: 0.5rem 0;
        font-weight: bold;
    }

    div {
        text-align: right;
    }

    a {
        color: rgb(0,100,200);
        text-decoration: none;
    }

    a:hover {
        text-decoration: underline; /* Adds underline on hover for better usability */
    }

    .tags {
        color: #007BFF;
        font-weight: bold;
    }
</style>
