<script>
    /** @type {import('./$types').PageData} */
    export let data;
</script>

<style>
    .aboutGrid {
        display: grid;
        grid-template-columns: 2fr 1fr;
        grid-template-rows: 30em auto;
        gap: 3em;
        padding-bottom: 10em;
    }

    .lastSupperImage {
        grid-column: 1 / 3;
        grid-row: 1 / 2;
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
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

<div class="aboutGrid">
    <img class="lastSupperImage" src="/lastSupper.webp" alt="Cream, Cartel Characters at the last supper">
        <div class="aboutCopy">
            <h1>About the Cream Cartel</h1>
            <h2>We deliver all along the east coast of Australia!</h2>
            <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Repellendus provident veritatis deleniti minus rerum voluptatibus totam eveniet saepe ab, facere asperiores, officia quos nihil molestias enim et nostrum, sunt omnis.</p>
        </div>
        <div class="tradingHours">
            <h3>Trading Hours</h3>
            <select id="category" class="catalogueDetailsSelect" on:change={(e) => updateDetails(e)}> 
                <option value="" disabled selected >Select your region</option>
                <option value="charger">Chargers</option>
                <option value="bundle">Bundles</option>
                <option value="flavoured">Flavoured</option>
                <option value="accessory">Accessories</option>
            </select>
            <p>Monday - Friday: 9am - 5pm</p>
            <p>Saturday: 10am - 4pm</p>
            <p>Sunday: Closed</p>
        </div>
</div>