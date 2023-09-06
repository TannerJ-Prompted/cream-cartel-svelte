<script>
    /** @type {import('./$types').PageData} */
    export let data;
</script>

<style>
    .aboutGrid {
        display: grid;
        grid-template-columns: 2fr 1fr;
        grid-template-rows: 30em auto;
    }

    .lastSupperImage {
        grid-column: 1 / 3;
        grid-row: 1 / 2;
        display: flex;
        justify-content: center;
        align-items: center;
    }

</style>

<div class="aboutGrid">
    <h3 class="lastSupperImage">Last supper image</h3>
        <div class="aboutCopy">
            <h1>About the Cream Cartel</h1>
            <h2>We deliver all along the east coast of Australia!</h2>
            <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Repellendus provident veritatis deleniti minus rerum voluptatibus totam eveniet saepe ab, facere asperiores, officia quos nihil molestias enim et nostrum, sunt omnis.</p>
        </div>
        <div class="tradingHours">
            <h3>Trading Hours</h3>
            <p>Monday - Friday: 9am - 5pm</p>
            <p>Saturday: 10am - 4pm</p>
            <p>Sunday: Closed</p>
        </div>
</div>