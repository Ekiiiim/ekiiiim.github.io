<script lang="ts">
	import { onMount } from 'svelte';

	let sections = ['About', 'Projects', 'Work', 'Life'];
	let currentSection = 'About';

	function handleScroll() {
		const sectionElements = document.querySelectorAll('section');
		const scrollPosition = window.scrollY + window.innerHeight / 2;

		sectionElements.forEach((section) => {
			if (
				scrollPosition >= section.offsetTop &&
				scrollPosition < section.offsetTop + section.offsetHeight
			) {
				currentSection = section.getAttribute('id') ?? '';
			}
		});
	}

	onMount(() => {
		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});
</script>

<div class="fixed top-0 left-0 h-full w-48 bg-gray-100 p-5 shadow-lg">
	{#each sections as section}
		<a
			href={`#${section}`}
			class={`mb-2 block rounded p-2 ${currentSection === section ? 'bg-blue-500 text-white' : 'text-gray-800'}`}
		>
			{section}
		</a>
	{/each}
</div>

<div class="ml-56 p-5">
	<section id="About" class="mb-10">
		<h1 class="text-2xl font-bold">About</h1>
		<p class=" h-screen">This is the about section.</p>
	</section>

	<section id="Projects" class="mb-10">
		<h1 class="text-2xl font-bold">Projects</h1>
		<p>Here are some of my projects.</p>
		<div class="h-screen">this should be in cards format...</div>
	</section>

	<section id="Work" class="mb-10">
		<h1 class="text-2xl font-bold">Work</h1>
		<p>Details about my professional work experience.</p>
		<div class="h-screen">timeline here...</div>
	</section>

	<section id="Life" class="mb-10 h-1/2">
		<h1 class="text-2xl font-bold">Life</h1>
		<blockquote class="border-l-4 border-blue-500 pl-4 italic">I will put a quote here</blockquote>
		<p class="h-screen">Frisbee, English Corner, Beatboxing...</p>
	</section>
</div>
