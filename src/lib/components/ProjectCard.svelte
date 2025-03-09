<script lang="ts">
	const title = 'Auto Valet Parking';
	const description =
		'Path planning for autonomous vehicle parking, using hybrid A* and optimization-based method to calculate trajectory.';
	const image = '/images/AutoValetParking.png';
	const url = 'https://github.com/Ekiiiim/AutomatedValetParking';

	const card = $state({
		flipped: false,
		flip() {
			this.flipped = !this.flipped;
		}
	});
</script>

<button
	onclick={() => card.flip()}
	class="h-48 w-72 cursor-pointer perspective-distant hover:scale-105"
>
	<div class="size-full duration-1000 transform-3d {card.flipped && 'rotate-y-180'}">
		<!-- front -->
		<div class="absolute inset-0 size-full backface-hidden">
			<div
				class="flex size-full flex-col items-center justify-center rounded-xl bg-gray-600/50 bg-blend-overlay"
				style="background-image: url({image}); background-size: cover; background-position: center;"
			>
				<div class="text-xl font-bold text-black">{title}</div>
			</div>
		</div>
		<!-- back -->
		<div class="absolute inset-0 size-full rotate-y-180 backface-hidden">
			<div class="flex size-full flex-col gap-1 rounded-xl bg-gray-200 p-3 dark:bg-gray-600">
				<div class="text-start text-xl font-bold">{title}</div>
				<div class="text-start">{description}</div>

				<a
					href={url}
					target="_blank"
					rel="noopener noreferrer"
					class="absolute bottom-3 text-start text-blue-500 hover:underline"
				>
					GitHub
				</a>
			</div>
		</div>
	</div></button
>
