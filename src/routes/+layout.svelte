<script>
    import {iosAppLink, androidAppLink} from '$lib/variables.js';
</script>

<div class="header">
    <div class="navBar">
        <a class="pirata shine gold" href="/">Cream Cartel</a>
        <a href="/catalogue">Catalogue</a>
        <a href="/about">About</a>
        <a href="#">Contact</a>
    </div>
    <div>
        <a href="{iosAppLink}" class="downloadButton">IOS</a>
        <a href="{androidAppLink}" class="downloadButton">ANDROID</a>
    </div>
</div>

<div class="contentContainer">
    <div class="content">
        <slot></slot>
    </div>
</div>

<div class="footer">
    <p>Copyright 2023</p>
    <div class="navBar">
        <a href="/documents/privacy-policy">Privacy Policy</a>
        <a href="/documents/terms-and-conditions">Terms & Conditions</a>
        <a href="/documents/returns-and-warranty">Returns & Warranty</a>
        <a href="/documents/product-safety">Product Safety</a>
    </div>
</div>