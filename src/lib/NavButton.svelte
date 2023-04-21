<script lang="ts">
    import { page } from '$app/stores';
    import { backgroundColor, accentColor } from '../colors';

    export let route: string;
    export let title: string;
	
    $: isActive = route === $page.url.pathname;;
    $: isActive == false, animateOut();

	let tick = 0;	
    let gradientState = `${backgroundColor}, ${backgroundColor}`
	let interval: any
	
    const createGradient = (colorIn: string, colorOut: string, percentage: number) => 
        `to right, ${colorIn} 0%, ${colorIn} ${percentage}%, ${colorOut} ${percentage}%, ${colorOut} 100%`

    const animateIn = () => {
            clearInterval(interval)
            tick = 0
            interval = setInterval(() => {
                tick <= 100 ? 
                    gradientState = createGradient(accentColor, backgroundColor, tick) :
                    gradientState = `${accentColor}, ${accentColor}`;
                tick = tick + 2
            }, 0.0001)
    }

    const animateOut = () => {
            clearInterval(interval)
            tick = 0
            interval = setInterval(() => {
                tick <= 100 ? 
                    gradientState = createGradient(backgroundColor, accentColor, tick) :
                    gradientState = `${backgroundColor}, ${backgroundColor}`;
                tick = tick + 2
            }, 0.0001)
    }
	
	$: if(tick >= 101) tick = 100
	$: if(tick < 0) tick = 0
</script>

{#if isActive}
    <div on:mouseleave={() => animateOut()}>
        <div class="element">
            <a href={route}
                style:border-style={`solid`}
                style:border-width={`0.1em`}
                style:border-image={`linear-gradient(${accentColor}, ${accentColor}) 0% 0 100% 0/0px 0 3px 0 stretch`}
                style:font-weight={`bolder`}
            >
                {title}
            </a>
        </div>
    </div>
{:else}
    <div on:mouseenter={() => {
            console.log(route + " animate IN")
            animateIn()
        }}
        on:mouseleave={() => {
            console.log(route + " animate OUT")
            animateOut()
        }}
        on:touchstart={() => {
            console.log(route + " animate IN")
            animateIn()
        }}
        on:touchend={() => {
            console.log(route + " animate OUT")
            animateOut()
        }}
    >
        <div class="element">
            <a href={route}
                style:border-style={`solid`}
                style:border-width={`0.1em`}
                style:border-image={`linear-gradient(${gradientState}) 0% 0 100% 0/0px 0 3px 0 stretch`}
            >
                {title}
            </a>
        </div>
    </div>
{/if}

<style>
    .element {
        display: block;
        padding: 10px;
        border: 0.1em solid transparent;
    }

    a {
        display: inline-block;
        margin: 0.6em 0;
        text-decoration: none;
        color: var(--text);
        font-size: 2vw;
    }

    a:hover {
        font-weight: bolder;
    }
</style>
