<script lang="ts">
	import '../app.css';
	let count = 0;
</script>

<h1 class="text-3xl">Counter: {count}</h1>
<button on:click={() => count++}>Increment</button>
<button on:click={() => count--}>Decrement</button>
<button on:click={() => (count = 0)}>Reset</button>
