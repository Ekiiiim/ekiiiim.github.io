<script lang="ts">
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	import ProjectCard from '$lib/components/ProjectCard.svelte';

	let sections = ['About', 'Projects', 'Work', 'Life'];
	let currentSection = '';

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
		handleScroll();
		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});
</script>

<div class="fixed z-[-1] min-h-screen min-w-screen dark:bg-gray-900"></div>

<div
	class="fixed top-0 left-0 flex h-full w-48 flex-col gap-2 bg-gray-100 p-5 shadow-lg dark:bg-white/10 dark:text-white"
>
	<div class="mb-5 flex w-full flex-col items-center gap-3">
		<img src="{base}/images/Mike_avatar.jpg" alt="Avatar" class="w-f rounded-full" />
		<span class="text-2xl font-bold">Mike Cheng</span>
	</div>
	{#each sections as section}
		<button
			on:click={() => {
				document.getElementById(section)?.scrollIntoView({ behavior: 'smooth' });
			}}
			class={`cursor-pointer rounded p-2 ${currentSection === section ? 'bg-blue-500 text-white' : 'text-gray-800 hover:bg-blue-200 dark:text-white dark:hover:bg-gray-600/50'}`}
		>
			{section}
		</button>
	{/each}
</div>

<div class="ml-56 p-5 dark:text-white">
	<section id="About" class="mb-10 scroll-mt-5">
		<h1 class="text-2xl font-bold">About</h1>
		<p class="h-screen">This is the about section.</p>
	</section>

	<section id="Projects" class="mb-10 scroll-mt-5">
		<h1 class="text-2xl font-bold">Projects</h1>
		<p>Here are some of my projects.</p>
		<div>this should be in cards format...</div>

		<div class="grid grid-cols-[repeat(auto-fill,_minmax(290px,_1fr))] gap-4 gap-y-8">
			<ProjectCard></ProjectCard>
			<ProjectCard></ProjectCard>
			<ProjectCard></ProjectCard>
			<ProjectCard></ProjectCard>
			<ProjectCard></ProjectCard>
		</div>
	</section>

	<section id="Work" class="mb-10 scroll-mt-5">
		<h1 class="text-2xl font-bold">Work</h1>
		<p>Details about my professional work experience.</p>
		<div class="h-screen">timeline here...</div>
	</section>

	<section id="Life" class="scroll-mt-5">
		<h1 class="text-2xl font-bold">Life</h1>
		<blockquote class="border-l-4 border-blue-500 pl-4 italic">I will put a quote here</blockquote>
		<p class="h-screen">Frisbee, English Corner, Beatboxing...</p>
	</section>
</div>
