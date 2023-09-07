<script>

    /** @type {import('./$types').PageData} */
    export let data;

    
    import products from '$lib/products.json';

    let details = false;

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

</style>

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
        {#each products.sheets[0].lines as item}
            <div class="card">
                <h3>{item.product_name}</h3>
            </div>
        {/each}
    </div>
</div>
{:else}
<div class="productGrid">
    {#each products.sheets[0].lines as item}
        <div class="card">
            <img src={item.product_image} alt="{item.product_name}">
            <h3>{item.product_name}</h3>
            <p>{item.product_description}</p>
            <p>{item.product_price}</p>
        </div>
    {/each}
</div>
{/if}