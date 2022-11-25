<template>
    <div class="footer-menu">
        <ul>
            <li>v0.2.0-rc</li>
            <li><RouterLink to="/about"
target="_blank">About</RouterLink></li>
            <li><a href="https://ko-fi.com/S6S0FY8A2">Support us!</a></li>
        </ul>
        <p>Provided and maintaned by <a href="http://lostcausegang.org"
target="_blank">Lost Cause Gang</a></p>
    </div>
</template>

<style>
.footer-menu {
    text-align: center;
    text-shadow: 1px 1px 4px rgba(79, 71, 50, 1);
    font-weight: 400;
}

.footer-menu,
.footer-menu a {
    color: #fff8e4;
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