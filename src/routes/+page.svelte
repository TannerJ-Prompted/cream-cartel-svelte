<script>
    /** @type {import('./$types').PageData} */
    export let data;
</script>

<style>

    .homeGrid h1 {
        font-size: 1.4rem;
        font-weight: 600;
        margin: 0;
        line-height: 1em;
        color: var(--CC-light)
    }
    .homeGrid{
        display: grid;
        grid-template-columns: 2fr 1fr;
        grid-template-rows: 1fr;
        padding-top: 8em;
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

</style>

<div class="homeGrid">
    <div class="heroColumn">
        <h1>The Cream Cartel</h1>
        <h2>Kitchen supplies delivered fast!</h2>
        <h3>Download our app today to get whipping!</h3>
        <div class="buttons">
            <a href="#" class="darkButton">Android</a>
            <a href="#" class="darkButton">iOS</a>
        </div>
    </div>
    <div class="cardsColumn">
        <p>Card</p>
        <p>Card</p>
    </div>
</div>