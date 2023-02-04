<script>
    import Footer from "../lib/footer.svelte";
    import Lobbies from "../lib/lobbies.svelte";
    import { Pname } from '../store.js';

    let name;

    Pname.subscribe((value) => {
		name = value;
	});

    const create = (par) => {
        const uuid = crypto.randomUUID().split('-')[1];
        
    }
    $: console.log(name);
</script>

<div class="">
    <div class="  bg-slate-600 pb-3">
        <h1 class=" p-8 flex justify-center text-8xl text-slate-300">
            TypeCircuit
        </h1>
        <h3 class=" p-3 flex justify-center text-5xl text-slate-50">
            A 2 player typing test, but you type the text
        </h3>
    </div>
    <div class="bg-slate-400 p-5">
        <input bind:value={name}>
        <button on:click={() => create()} class="p-2 bg-red-200 rounded">Create New Game</button>
    </div>
    <Lobbies />
    <Footer />
</div>

<style>


</style>