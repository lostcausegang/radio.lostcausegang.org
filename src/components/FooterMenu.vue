<template>
    <div class="footer-menu">
        <ul>
            <li>v0.3.1</li>
            <li>
                <RouterLink to="/about">About</RouterLink>
            </li>
            <li>
                <RouterLink to="/how-to-listen">How to listen</RouterLink>
            </li>
            <li>
                <RouterLink to="/privacy">Privacy Policy</RouterLink>
            </li>
            <li>
                <a href="https://github.com/lostcausegang/radio.lostcausegang.org" target="_blank">Source code</a>
            </li>
        </ul>
        <p>Provided and maintained by <a href="http://lostcausegang.org" target="_blank">Lost Cause Gang</a></p>
    </div>
</template>

<style>
.footer-menu {
    text-align: center;
    font-weight: 400;
    /* position: fixed; */
    bottom: 1em;
    width: 100%;
}

.footer-menu,
.footer-menu a {
    color: black;
}

.footer-menu ul {
    margin: 0;
    padding: 0;
}

.footer-menu ul li {
    list-style-type: none;
    display: inline;
}

.footer-menu li:not(:first-child)::before {
    content: " | ";
}
</style>
