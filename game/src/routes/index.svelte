<script context="module">

    export const prerender = true

</script>
<script>
    import CheckoutOtherProjects from '../components/CheckoutOtherProjects.svelte'
    import StockGraphView from '../components/StockGraphView.svelte'
    import { goto } from '$app/navigation'
    import { PaperTradingGame } from '../logic/game'

    const exampleGame = PaperTradingGame.newGame('')
    exampleGame.priceData[exampleGame.priceData.length - 1] = exampleGame.priceData[exampleGame.priceData.length - 2] + 1
    const github = 'https://github.com/davjhan/paper-trader-game'
</script>
<svelte:head>
    <script async defer src="https://buttons.github.io/buttons.js"></script>
</svelte:head>
<style>
    button {
        touch-action: manipulation;
    }
</style>
<main class='p-4 flex flex-col '>
    <div class="inline-flex items-start mt-2 self-end ">
        <a href={github} class='ml-1 mr-2 underline text-gray-dark text-sm'>Big thanks to davjhan source code (Github) for this project</a>
    </div>
    <h1 class='mt-4 mb-1 self-center'>SafeMoon Trading Game</h1>
    <h4 class='mb-8 self-center text-sm'>(Duration: 45s)</h4>
    <button class='reg my-4 self-center w-40 animate-throb' on:click={()=>goto('/game')}>Start Game</button>

    <span class='mb-2 font-semibold text-gray-500'>How to play</span>
    <ol class='mb-4 ml-2 list-decimal list-inside'>
        <li>
            You are given <b>$1000</b> dollars and a fake, simulated
            price of SafeMoon.
        </li>
        <li>
            Make as much money as you can in <b>45 seconds</b>.
        </li>
    </ol>
    <span class='italic mb-2 font-semibold text-gray-500'>Example:</span>
    <div class="border-2 rounded border-black p-4">
        <StockGraphView priceData={exampleGame.priceData} holdsPosition={true}/>
    </div>
    <CheckoutOtherProjects class='mt-12'/>
</main>