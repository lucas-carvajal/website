<script lang="ts">
    import "@fontsource/montserrat"
    import NavButton from "../lib/NavButton.svelte"
</script>

<div class="nav">
    <div class="elements">
        <NavButton route="/" title="Lucas" />
        <NavButton route="/work" title="Work" />
        <NavButton route="/education" title="Education" />
        <NavButton route="/projects" title="Projects" />
        <NavButton route="/contact" title="Contact" />
    </div>
</div>

<div class="main">
    <slot></slot>
</div>

<style>
    .nav {
        position: fixed;
        width: 20%;
        height: 100%;
        top: 0;
        left: 0;
        z-index: 1;
        overflow-x: hidden;
        padding-top: auto;
        padding-bottom: auto;
        padding-left: 20px;
        display: flex;
        justify-content: center;
        align-items: center; 
    }

    .main {
        margin-left: 20%;
        padding: 4em;
    }

    div {
        font-family: 'montserrat', sans-serif;
    }
</style>
