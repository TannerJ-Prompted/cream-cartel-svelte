<script>
    import {iosAppLink, androidAppLink} from '$lib/variables.js';

    let mobileMenuActive = false;
</script>

<style>

:root {
	--CC-dark: #1a1a1a;
	--CC-mid: #686868;
	--CC-light: #cccccc;
	--CC-white: #ffffff;
	--CC-gold: #ecb653;
	--fiend-red: #e12d2d;
	--cosmic-green: #63d471;
}

html {
	box-sizing: border-box;
	font-family: 'Poppins', sans-serif;
	background-color: var(--CC-mid);
	background-image: url('/chargerPattern.png');
	background-position: center top;
	background-repeat: repeat;
	background-size: 500px;
}

body {
	margin: 0em;
}

* {
	box-sizing: border-box;
	transition: all 0.2s ease-in-out;
}

div {
	font-size: 14px;
	padding: 0.2em;
	border-radius: 0.8em;
	color: black;
}

a {
	border-radius: 0.8em;
	padding: 0.8em;
	color: var(--CC-white);
	text-decoration: none;
	text-transform: uppercase;
}

a:hover {
	color: var(--CC-gold);
}

h1,
h2,
h3,
h4,
h5,
h6,
p {
	color: var(--CC-white);
	letter-spacing: 0.03em;
}

h2 {
	font-size: 4em;
	text-transform: uppercase;
	line-height: 1em;
}

h3 {
	color: var(--CC-light);
	font-size: 2em;
	text-transform: uppercase;
	line-height: 1em;
}

p {
	font-weight: 400;
}

li {
	color: var(--CC-light);
}

.gold {
	color: var(--CC-gold);
}

.pirata {
	font-family: 'Pirata One', 'Poppins', sans-serif;
	font-size: 2em;
	font-style: italic;
}

.header,
.footer {
	display: flex;
	justify-content: space-between;
	align-items: center;
	background-color: var(--CC-dark);
	padding: 0.2em 2em;
}

.header {
	position: sticky;
	width: calc(100% - 2em);
	top: 1em;
	margin-left: auto;
	margin-right: auto;
}

.header a {
	padding: 0.3em;
}

.footer {
	width: 100%;
	position: fixed;
	bottom: 0em;
	border-radius: 0em;
}

.footer a,
.footer p {
	padding: 0em;
	margin: 0em;
}

.navBar {
	display: flex;
	justify-content: flex-start;
	align-items: center;
	gap: 2em;
}

.contentContainer {
	display: flex;
	justify-content: flex-start;
	align-items: center;
	flex-direction: column;
	gap: 2em;
}

.content {
	width: 100%;
	max-width: 1140px;
}

.darkButton {
	background-color: var(--CC-dark);
	color: var(--CC-light);
	min-width: 10em;
	text-align: center;
	font-weight: 600;
	font-size: 1.3em;
}

.darkButton:hover {
	background-color: var(--CC-gold);
	color: var(--CC-dark);
}

a.downloadButton {
	background-color: var(--CC-gold);
	color: var(--CC-dark);
	min-width: 10em;
	text-align: center;
	font-weight: 600;
	font-size: 1.3em;
	padding: 0.5em 2em;
}

a.downloadButton:hover {
	background-color: var(--CC-light);
	color: var(--CC-dark);
}

.shine {
	overflow: hidden;
	position: relative;
}

.shine::before {
	content: '';
	position: absolute;
	width: 100px;
	height: 100%;
	background-image: linear-gradient(
		120deg,
		rgba(255, 255, 255, 0) 30%,
		rgb(255, 255, 255),
		rgba(255, 255, 255, 0) 70%
	);
	top: 0;
	left: -100px;
	animation: shine 1s 3 linear;
	animation-delay: 2s;
}

@keyframes shine {
	0% {
		left: -100px;
	}
	20% {
		left: 100%;
	}
	100% {
		left: 100%;
	}
}

.shadow {
	box-shadow: 0px 2px 2px 2px rgba(0, 0, 0, 0.15);
}

#menuButton {
	display: none;
	background-color: var(--CC-light);
}

@media only screen and (max-width: 850px) {
	.header {
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		flex-wrap: wrap;
	}
	.navBar {
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}
	.contentContainer {
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	.content {
		width: 100%;
		max-width: 100%;
	}
	.darkButton {
		font-size: 1em;
	}
	.darkButton:hover {
		font-size: 1em;
	}
	a.downloadButton {
		font-size: 1em;
		padding: 0.5em 1em;
	}
	a.downloadButton:hover {
		font-size: 1em;
	}
}

@media only screen and (max-width: 720px) {
	.navBar a {
		display: none;
	}
	.navBar .pirata {
		display: block;
	}

	#menuButton {
		display: inline;
	}

	.footer {
		display: none;
	}
}

@media only screen and (max-width: 500px) {
	.navBar a {
		display: none;
	}
	.navBar .pirata {
		display: block;
	}

	.downloadButton {
		display: none;
	}

	#menuButton {
		display: inline;
	}

	.footer {
		display: none;
	}
}


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