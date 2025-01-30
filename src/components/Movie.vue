<template>
    <article @click="$emit('deleteMovie')"
    :class="{'seen': movie.seen, 'not-seen': !movie.seen }"
    >
        <h3>{{ movie.name }} ({{ movie.year }})</h3>
    </article>
</template>

<script>
export default {
    props: {
        movie: Object
    }
}
</script>

<style>
article {
    width: 100%;
    height: 80px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: rgb(201, 201, 201);
    border-radius: 3px;
}

article:hover {
    background-color: rgb(220,220,220);
    cursor: pointer;
}

h3 {
    color: rgb(26,26,26);
}

.seen {
    border: 2px solid rgb(66,185,130);
}

.not-seen {
    border: 2px solid rgb(255, 110, 110);
}

</style>