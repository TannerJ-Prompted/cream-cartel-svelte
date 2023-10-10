<script>
        /** @type {import('./$types').PageData} */
        export let data;
        import { page } from '$app/stores';
        import products from '$lib/products.json';
        import { locations, androidAppLink, iosAppLink } from '$lib/variables.js';
	    import { onMount } from 'svelte';

        let pageId = $page.params.category;



</script>

<style>
    .catalogueGrid{
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-template-rows: 1fr;
    }

    .heroColumn{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: flex-start;
        padding: 0 2rem;
    }

    .buttons {
        display: flex;
        flex-direction: row;
        justify-content: flex-start;
        align-items: center;
        gap: 2em;
    }

    .productGrid {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr;
        grid-template-rows: auto;
        gap: 2em;
        padding: 10em 2em;
    }

    .card {
        width: 100%;
        max-width: 100%;
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        align-items: flex-start;
        background-color: var(--CC-light);
        border-radius: 1rem;
        padding: 1.3rem;
        gap: 0.5em;
    }

    .card img {
        aspect-ratio: 1 / 1;
        width: 100%;
        background-color: var(--CC-dark);
        border-radius: 0.8em;
    }

    .productImage {
        border-bottom: 0.3em solid var(--CC-dark);
    }

    .card h3 {
        font-size: 1.5rem;
        font-weight: 800;
        color: var(--CC-dark);
        text-align: left;
        margin: 0em;
    }

    .card p {
        color: var(--CC-dark);
        font-weight: 600;
        margin: 0em;
    }

    .card ul {
        list-style: none;
        padding: 0;
        margin: 0;
        display: flex;
        flex-direction: row;
        justify-content: flex-start;
        flex-wrap: wrap;
        align-items: center;
        gap: 0.5em;
    }

    .card li.location {
        background-color: var(--CC-dark);
        border-radius: 0.5em;
        padding: 0.5em 1em;
        border: none;
        color: var(--CC-light);
        font-weight: 600;
        font-size: 0.8em;
        text-transform: uppercase;
    }

    .card img.tinyLogo {
        aspect-ratio: 1 / 1;
        width: 3em;
        background-color: transparent;
        border-radius: 0em;
    }

    .catalogueDetailsBar {
        padding: 0.75em 2em;
        position: sticky;
        top: 6em;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: row;
        gap: 2em;
    }

    .catalogueCategory {
        background-color: var(--CC-gold);
        border-radius: 0.5em;
        padding: 0.5em 1em;
        border: none;
        color: var(--CC-dark);
        font-weight: 600;
        font-size: 1.2em;
        text-transform: uppercase;
        transition: all 0.2s ease-in-out;
    }

    .catalogueCategory:hover {
        background-color: var(--CC-dark);
        color: var(--CC-light)
    }

    .active {
        background-color: var(--CC-dark);
        color: var(--CC-light);
    }

    .appDownloadDialogue {
        position: sticky;
        bottom: 4em;
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        background-color: var(--CC-dark);
        padding: 2em;
        gap: 2em;
    }
    
    .appDownloadDialogue h3{
        margin: 0em;
    }

</style>

<div class="catalogueDetailsBar">
    <a class="catalogueCategory shadow" href="/catalogue/bundles" class:active={$page.params.category==="bundles"}>Bundles</a>
    <a class="catalogueCategory shadow" href="/catalogue/chargers" class:active={$page.params.category==="chargers"}>Chargers</a>
    <a class="catalogueCategory shadow" href="/catalogue/tanks" class:active={$page.params.category==="tanks"}>Tanks</a>
    <a class="catalogueCategory shadow" href="/catalogue/flavoured" class:active={$page.params.category==="flavoured"}>Flavoured</a>
    <a class="catalogueCategory shadow" href="/catalogue/accessories" class:active={$page.params.category==="accessories"}>Accessories</a>
</div>
<div class="productGrid">
    {#each products.sheets[0].lines as item}
        {#if item.category.includes($page.params.category)}
            <div class="card shadow">
                <img class="productImage" src={`/productImages/${item.product_image}`} alt="{item.product_name}">
                <h3>{item.product_name}</h3>
                <p>{item.product_description}</p>
                <ul>
                    {#each item.region as location}
                        <li class="location">{location}</li>
                    {/each}
                </ul>
                <ul>
                    {#each item.branch as branch}
                        {#if branch === "fiend"}
                            <img class="tinyLogo" src="/fiendLogoTiny.webp" alt="Fiend">
                        {:else if branch === "cosmic"}
                            <img class="tinyLogo" src="/cosmicLogoTiny.webp" alt="Cosmic">
                        {/if}
                    {/each}
                </ul>
            </div>
        {/if}
    {/each}
</div>
<div class="appDownloadDialogue">
    <h3>If you'd like to make a purchase, download our app!</h3>
    <div class="buttons">
        <a href="{androidAppLink}" class="downloadButton">Android</a>
        <a href="{iosAppLink}" class="downloadButton">iOS</a>
    </div>
</div>