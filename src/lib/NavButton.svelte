<script lang="ts">
    export let route: string;
    export let title: string;
</script>

<div class="element">
    <a href={route}>{title}</a>
</div>

<style>
    .element {
        display: block;
        padding: 10px;
    }

    a {
        display: inline-block;
        margin: 0.6em 0;
        text-decoration: none;
        color: black;
        font-size: 2vw;
        letter-spacing: 1px;
    }

    a:hover {
        font-weight: bolder;
        letter-spacing: 0px;
        border-bottom: 0.1em solid black;
    }
</style>
<!--  TODO border animation: https://svelte.dev/repl/e8f01306bf904a09b72d631816d55775?version=3.50.1 -->
