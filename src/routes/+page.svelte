<script lang="ts">
	import { imageData } from '../core/data/images';
	import type Image from '../core/models/image';
	import { onMount } from 'svelte';

	let imagesToDisplay: Image[] = [];

	onMount(() => {
		getRandomImages();
	});

	const getRandomImages = () => {
		imagesToDisplay.length = 0;

		imagesToDisplay.push(getRandomImageFromArray());
		imagesToDisplay.push(getRandomImageFromArray());
	};

	const getRandomImageFromArray = (): Image => {
		return imageData[Math.floor(Math.random() * imageData.length)];
	};
</script>

<div class="p-8 ">
	<h1 class="font-bold text-6xl uppercase">Amin Osman</h1>
	<h2 class="italic text-6xl mt-2 uppercase">Portfolio</h2>
</div>

<div class="w-full flex flex-wrap gap-x-8">
	<p class="mt-8 pl-8 xl:w-1/3 max-w-md">
		Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt
		ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo
		dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor
		sit amet.
	</p>
	<div class="flex-1">
		<div class="flex justify-center mb-8">
			<div class="flex items-center flex-col">
				<p class="font-light">refresh</p>
				<button
					class="p-4 mt-2 bg-gray-200 hover:bg-gray-300 transition-all rounded-full"
					on:click={getRandomImages}
					><img src="/images/pfeil.svg" alt="arrow" class="h-8 w-8" /></button
				>
			</div>
		</div>
		{#if imagesToDisplay.length}
			<div class="flex gap-x-4 h-[500px] overflow-hidden w-full justify-center xl:p-0 p-8">
				<div class="flex-col flex justify-end">
					<img
						alt={imagesToDisplay[0].title}
						src={imagesToDisplay[0].url}
						class=" max-w-sm w-full h-auto"
					/>
					<p>
						{imagesToDisplay[0].title},{imagesToDisplay[0].year},{imagesToDisplay[0]
							.material},{imagesToDisplay[0].mass}
					</p>
				</div>

				<div class="h-full flex flex-col items-center">
					<div class="w-[1px] h-full bg-black " />
				</div>

				<div class="flex-col flex justify-end">
					<div class="relative ">
						<img
							alt={imagesToDisplay[1].title}
							src={imagesToDisplay[1].url}
							class="max-w-sm w-full h-auto"
						/>
					</div>
					<p class="">
						{imagesToDisplay[1].title},{imagesToDisplay[1].year},{imagesToDisplay[1]
							.material},{imagesToDisplay[1].mass}
					</p>
				</div>
			</div>
		{/if}
	</div>
</div>
