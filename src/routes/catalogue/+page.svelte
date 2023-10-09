<script>

    /** @type {import('./$types').PageData} */
    export let data;

    
    import products from '$lib/products.json';
    import { locations } from '$lib/variables.js';
	import { onMount } from 'svelte';

    let details = true;
    let region = "";
    let branch = "";
    let category = "";
    let itemPrice = "";
    let itemImageString = "";
    
    function updateDetails(e) {
        if (e.target.id == "region") {
            region = e.target.value;
            itemPrice = `${e.target.value}_price`;
        } else if (e.target.id == "branch") {
            branch = e.target.value;
            itemImageString = `${e.target.value}_image`
            console.log(itemImageString)
        } else if (e.target.id == "category") {
            category = e.target.value;
        }

        if (region != "" && branch != "" && category != "") {
            details = false;
        }
    }

    onMount(() => {
        console.log(products, locations);
    });

</script>

<style>
    .catalogueGrid{
        margin-top: 10em;
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
        padding: 10em 2em;;
    }

    .card {
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        align-items: flex-start;
        background-color: var(--CC-light);
        border-radius: 1rem;
        padding: 1.3rem;
    }

    .card img {
        aspect-ratio: 1 / 1;
        width: 100%;
        background-color: var(--CC-dark);
        border-radius: 0.8em;
    }

    .card h3 {
        font-size: 1.5rem;
        font-weight: 800;
        color: var(--CC-dark);
        text-align: left;
        margin-bottom: 0em;;
    }

    .card p {
        color: var(--CC-dark);
        font-weight: 600;
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

</style>

<div class="catalogueDetailsBar">
    <a class="catalogueCategory" href="/catalogue/chargers">Chargers</a>
    <a class="catalogueCategory" href="/catalogue/flavoured">Flavoured</a>
    <a class="catalogueCategory" href="/catalogue/bundles">Bundles</a>
    <a class="catalogueCategory" href="/catalogue/accessories">Accessories</a>
</div>
<div class="catalogueGrid">
    <div class="heroColumn">
        <h2>See what we have on offer!</h2>
        <h3>Or browse our catalogue through our app!</h3>
        <div class="buttons">
            <a href="#" class="darkButton">Android</a>
            <a href="#" class="darkButton">iOS</a>
        </div>
    </div>
    <div class="cardsColumn">
    </div>
</div>