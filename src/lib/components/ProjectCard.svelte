<script lang="ts">
	const card = $state({
		flipped: false,
		flip() {
			this.flipped = !this.flipped;
		}
	});
</script>

<button onclick={() => card.flip()} class="h-48 w-72 cursor-pointer perspective-distant">
	<div
		class="size-full duration-1000 transform-3d dark:text-white {card.flipped && 'rotate-y-180'}"
	>
		<!-- front -->
		<div class="absolute inset-0 size-full backface-hidden">
			<div class="flex size-full flex-col items-center justify-center rounded-xl bg-gray-200/10">
				Front
			</div>
		</div>
		<!-- back -->
		<div class="absolute inset-0 size-full rotate-y-180 backface-hidden">
			<div class="flex size-full flex-col items-center justify-center rounded-xl bg-gray-600">
				Back
			</div>
		</div>
	</div>
</button>
