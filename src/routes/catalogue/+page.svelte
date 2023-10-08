<script>

    /** @type {import('./$types').PageData} */
    export let data;

    
    import products from '$lib/products.json';
	import { onMount } from 'svelte';

    let details = true;
    let region = "";
    let branch = "";
    let category = "";
    let itemPrice = "";
    
    function updateDetails(e) {
        if (e.target.id == "region") {
            region = e.target.value;
            itemPrice = `${e.target.value}_price`;
        } else if (e.target.id == "branch") {
            branch = e.target.value;
        } else if (e.target.id == "category") {
            category = e.target.value;
        }

        if (region != "" && branch != "" && category != "") {
            details = false;
        }
    }

    onMount(() => {
        console.log(products);
    });

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
        width: 100%;
        background-color: var(--CC-dark);
        padding: 0.75em 2em;
        position: sticky;
        top: 6em;
        display:flex;
        justify-content: flex-start;
        align-items: center;
        flex-direction: row;
        gap: 2em;
    }

    .catalogueDetailsSelect {
        background-color: var(--CC-light);
        border-radius: 0.5em;
        padding: 0.5em 1em;
        border: none;
        color: var(--CC-dark);
        font-weight: 600;
        font-size: 0.8rem;
        text-transform: uppercase;
    }

</style>

<div class="catalogueDetailsBar">
    <select id="region" class="catalogueDetailsSelect" on:change={(e) => updateDetails(e)}>
        <option value="" disabled selected >Select your region</option>
        <option value="sydney">Sydney</option>
        <option value="newcastle">Newcastle</option>
        <option value="canberra">Canberra</option>
        <option value="canberra">Port Stephens</option>
    </select>
    <select id="branch" class="catalogueDetailsSelect" on:change={(e) => updateDetails(e)}>
        <option value="" disabled selected >Select your branch</option>
        <option value="fiend">Cream Fiend</option>
        <option value="cosmic">Cosmic Cream</option>
    </select>
    <select id="category" class="catalogueDetailsSelect" on:change={(e) => updateDetails(e)}> 
        <option value="" disabled selected >Select your category</option>
        <option value="charger">Chargers</option>
        <option value="bundle">Bundles</option>
        <option value="flavoured">Flavoured</option>
        <option value="accessory">Accessories</option>
    </select>
</div>
{#if details}
<div class="catalogueGrid">
    <div class="heroColumn">
        <h2>Select your region, branch, and category</h2>
        <h3>Or browse our catalogue through our app!</h3>
        <div class="buttons">
            <a href="#" class="darkButton">Android</a>
            <a href="#" class="darkButton">iOS</a>
        </div>
    </div>
    <div class="cardsColumn">
    </div>
</div>
{:else}
<div class="productGrid">
    {#each products.sheets[0].lines as item}
        {#if item.region.includes(region) && item.branch.includes(branch) && item.category.includes(category)}
        <div class="card">
            <img src={item.product_image} alt="{item.product_name}">
            <h3>{item.product_name}</h3>
            <p>{item.product_description}</p>
            <p>{item[itemPrice]}</p>
        </div>
        {/if}
    {/each}
</div>
{/if}