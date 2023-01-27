<script lang="ts">
    export let route: string;
    export let title: string;
	
	// State
	let tick = 0;	
	let gradientState = `white, white`
	let interval: any
	
    const createGradient = (percentage: number) => 
        `to right, black 0%, black ${percentage}%, white ${percentage}%, white 100%`

    let gr1 = `to right, black 0%, black 47%, white 47%, white 100%`;
    let colorr = 'orange';

	const animation = (direction: number) => {
			clearInterval(interval)
			interval = setInterval(() => {
				tick <= 100 ? 
					gradientState = createGradient(tick) :
			  	    gradientState = `black, black`;
				direction === 1 ? 
                    tick = tick + 2 :
                    tick = tick - 2;
                console.log(gradientState)
			}, 10)
	}
	
	$: if(tick >= 101) tick = 100
	$: if(tick < 0) tick = 0
</script>

<div on:mouseenter={() => animation(1)}
    on:mouseleave={() => animation(0)}
>
    <div class="element">
        <a href={route} style:background={`linear-gradient(${gradientState}) left bottom white no-repeat`}>
        <!-- <a href={route} 
            style:border-bottom={`0.1em solid linear-gradient(to right, black 0%, black 47%, white 47%, white 100%)`}    
            style:border-color={`linear-gradient(orange, red)`}
            style:border-image-slice={`1`}
        > -->
            {title}
        </a>
    </div>
</div>

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
        color: black;
        font-size: 2vw;
        padding-bottom: 0.1em;
        /* background: linear-gradient(to right, black 0%, black 47%, white 47%, white 100%) bottom white no-repeat; */
        background-size: 100% 0.1em;
        /* letter-spacing: 1px; */
    }

    a:hover {
        font-weight: bolder;
        /* letter-spacing: 0px; */
        /* border-bottom: 0.1em solid black; */
    }
</style>

<!-- TODO: https://svelte.dev/repl/e8f01306bf904a09b72d631816d55775?version=3.50.1 -->
