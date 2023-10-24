<script>
    import {iosAppLink, androidAppLink} from '$lib/variables.js';

    let mobileMenuActive = false;
</script>

<style>

.offScreenMobileMenu {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background-color: var(--CC-light);
    z-index: 100;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 2em;
    padding: 2em;
    transform: translateX(-100%);
    transition: transform 0.3s ease-in-out;
}


.offScreenMobileMenu a {
    font-size: 2em;
    font-weight: 800;
    color: var(--CC-dark);
    text-decoration: none;
    transition: all 0.2s ease-in-out;
}

.offScreenMobileMenu a:hover {
    color: var(--CC-gold);
}

.offScreenMobileMenu.active {
    transform: translateX(0%);
}

.offScreenMobileMenu .closeButton {
    position: absolute;
    top: 1em;
    right: 1em;
    font-size: 2em;
    font-weight: 800;
    color: var(--CC-dark);
    text-decoration: none;
    transition: all 0.2s ease-in-out;
}

.offScreenMobileMenu .footerLinks {
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    align-items: center;
    flex-wrap: wrap;
    gap: 0em;
    background-color: var(--CC-dark);
    padding: 0em 1em;
}

.offScreenMobileMenu .footerLinks a {
    font-size: 1em;
    font-weight: bold;
    color: var(--CC-light);
    text-decoration: none;
    transition: all 0.2s ease-in-out;
}
</style>

<div class:active={mobileMenuActive} class="offScreenMobileMenu">
    <a on:click={() => mobileMenuActive = !mobileMenuActive} href="/">Home</a>
    <a on:click={() => mobileMenuActive = !mobileMenuActive} href="/catalogue">Catalogue</a>
    <a on:click={() => mobileMenuActive = !mobileMenuActive} href="/about">About</a>
    <a on:click={() => mobileMenuActive = !mobileMenuActive} href="#">Contact</a>
    <a on:click={() => mobileMenuActive = !mobileMenuActive} href="{iosAppLink}">IOS</a>
    <a on:click={() => mobileMenuActive = !mobileMenuActive} href="{androidAppLink}">ANDROID</a>
    <a on:click={() => mobileMenuActive = !mobileMenuActive} href="#" class="closeButton">X</a>
    <div class="footerLinks">
        <a on:click={() => mobileMenuActive = !mobileMenuActive} href="/documents/privacy-policy">Privacy Policy</a>
        <a on:click={() => mobileMenuActive = !mobileMenuActive} href="/documents/terms-and-conditions">Terms & Conditions</a>
        <a on:click={() => mobileMenuActive = !mobileMenuActive} href="/documents/returns-and-warranty">Returns & Warranty</a>
        <a on:click={() => mobileMenuActive = !mobileMenuActive} href="/documents/product-safety">Product Safety</a>
        <a on:click={() => mobileMenuActive = !mobileMenuActive} href="/documents/cookie-policy">Cookie Policy</a>
    </div>
</div>
<div class="header shadow">
    <div class="navBar">
        <a class="pirata shine gold" href="/">Cream Cartel</a>
        <a href="/catalogue">Catalogue</a>
        <a href="/about">About</a>
        <a href="#">Contact</a>
    </div>
    <div>
        <a href="{iosAppLink}" class="downloadButton">IOS</a>
        <a href="{androidAppLink}" class="downloadButton">ANDROID</a>
        <a href="#" id="menuButton" class="downloadButton" on:click={() => mobileMenuActive = !mobileMenuActive}>Menu</a>
    </div>
</div>

<div class="contentContainer">
    <div class="content">
        <slot></slot>
    </div>
</div>

<div class="footer">
    <p>All content and imagery on this site is subject to copyright</p>
    <div class="navBar">
        <a href="/documents/privacy-policy">Privacy Policy</a>
        <a href="/documents/terms-and-conditions">Terms & Conditions</a>
        <a href="/documents/returns-and-warranty">Returns & Warranty</a>
        <a href="/documents/product-safety">Product Safety</a>
        <a href="/documents/cookie-policy">Cookie Policy</a>
    </div>
</div>