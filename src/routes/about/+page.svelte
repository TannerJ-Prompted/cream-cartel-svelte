<script>
    /** @type {import('./$types').PageData} */
    export let data;

    import { locations } from '$lib/variables.js';

    let region = "";

    function updateDetails(e) {
            region = locations.filter(location => location.value == e.target.value)[0];
    };
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
        background-color: var(--CC-gold);
        border-radius: 0.5em;
        padding: 0.5em 1em;
        border: none;
        color: var(--CC-dark);
        font-weight: 600;
        font-size: 1em;
        text-transform: uppercase;
    }

    @media only screen and (max-width:800px){
        .aboutGrid {
            grid-template-columns: 1fr;
            grid-template-rows: auto auto auto;
            gap: 3em;
            padding: 1em;
            padding-top: 3em;
            padding-bottom: 10em;
        }

        .lastSupperImage {
            grid-column: 1 / 2;
            grid-row: 1 / 2;
            display: flex;
            justify-content: center;
            align-items: center;
            width: 100%;
        }

        .aboutCopy {
            grid-column: 1 / 2;
            grid-row: 2 / 3;
        }

        .tradingHours {
            grid-column: 1 / 2;
            grid-row: 3 / 4;
        }
    }

</style>

<div class="aboutGrid">
    <img class="lastSupperImage" src="/lastSupper.webp" alt="Cream, Cartel Characters at the last supper">
        <div class="aboutCopy">
            <h1>About the Cream Cartel</h1>
            <h2>We deliver all along the east coast of Australia!</h2>
            <p>Welcome to The Cream Cartel, your trusted partner for all your kitchen supply needs, specializing in after-hours delivery of premium baking essentials and delectable whipped cream. We are more than just a delivery service; we are your dedicated allies in the pursuit of culinary perfection.</p>
            <h3>Our Passion for Baking and Cream</h3>
            <p>At The Cream Cartel, our love for baking runs deep, and we understand the importance of having the right ingredients at your fingertips, especially when inspiration strikes late at night. We are committed to making your baking dreams come true by providing a convenient and reliable source for top-quality kitchen supplies, any time you need them.</p>
            <h3>Why Choose The Cream Cartel?</h3>
            <h4>Late-Night Delights:</h4>
            <p>We know that creativity knows no schedule. That's why we operate well into the night, ensuring that you can access your favorite baking ingredients and whipped cream whenever the craving strikes.</p>
            <h4>Premium Quality</h4>
            <p>We take pride in sourcing only the finest ingredients and products for our customers. From premium flours and sugars to the creamiest whipped toppings, we are your go-to source for the best of the best.</p>
            <h4>Fast and Reliable</h4>
            <p>Our dedicated team of delivery experts is committed to providing speedy and reliable service. We understand that when you need supplies, you need them now.</p>
            <h4>Wide Selection</h4>
            <p>Whether you're a seasoned pastry chef or a home baking enthusiast, our extensive range of products caters to all skill levels and preferences. From baking basics to specialty items, we have it all.</p>
            <h4>Customer-Centric</h4>
            <p>Your satisfaction is our top priority. We go the extra mile to ensure that your orders are accurate, well-packaged, and delivered with a smile. Our customer support team is always ready to assist you with any queries or concerns.</p>
            <h3>Join The Cream Cartel Family</h3>
            <p>We invite you to experience the convenience and quality that The Cream Cartel offers. Whether you're preparing for a late-night baking session, a special celebration, or simply looking to indulge in the finest whipped cream, we're here for you.

                Thank you for choosing The Cream Cartel as your trusted partner for kitchen supplies. We look forward to serving you and being a part of your culinary adventures. Together, let's whip up something extraordinary!</p>
        </div>
        <div class="tradingHours">
            <h3>Trading Hours</h3>
            <select id="region" class="catalogueDetailsSelect" on:change={(e) => updateDetails(e)}> 
                <option value="" disabled selected >Select your region</option>
                {#each locations as { name, value }}
                    <option value={value}>{name}</option>
                {/each}
            </select>
            {#if region != ""}
                {#each region.tradingHours as { day, hours}}
                    <p>{day}: {hours}</p>
                {/each}
            {/if}
        </div>
</div>