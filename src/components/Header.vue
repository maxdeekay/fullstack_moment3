<template>
    <header>
        <div class="header-wrapper">
            <h1>Moment 3</h1>
            <nav>
                <ul>
                    <li><RouterLink to="/" exact-active-class="active">Hem</RouterLink></li>
                    <li><RouterLink to="/movies" exact-active-class="active">Filmer</RouterLink></li>
                    <li><RouterLink to="/info" exact-active-class="active">Info</RouterLink></li>
                </ul>
            </nav>
        </div>
    </header>
</template>

<script>
import { RouterLink } from "vue-router";

export default {
    name: "Header"   
}
</script>

<style scoped>
header {
    padding: 10px 20px;
}

.header-wrapper {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

ul {
    display: flex;
    list-style-type: none;
    gap: 40px;
}

a {
    color: rgb(66,185,130);
    text-decoration: none;
    font-size: 22px;
}

a:hover {
    color: rgb(219,218,218);
}

.active {
    color: rgb(219,218,218);
}
</style>