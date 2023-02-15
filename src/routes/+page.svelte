<script lang="ts">
	import { imageData } from '../core/data/images';
	import type Image from '../core/models/image';
	import { onMount } from 'svelte';

	let imagesToDisplay: Image[] = [];

	let isIconRotated = false;

	onMount(() => {
		getRandomImages();
	});

	const getRandomImages = () => {
		imagesToDisplay.length = 0;
		isIconRotated = true;
		console.log(isIconRotated);
		imagesToDisplay.push(getRandomImageFromArray());
		imagesToDisplay.push(getRandomImageFromArray());
		isIconRotated = false;
	};

	const getRandomImageFromArray = (): Image => {
		return imageData[Math.floor(Math.random() * imageData.length)];
	};
</script>

<div class="block lg:flex">
	<div class="lg:p-8 p-2 xl:w-1/3 max-w-lg">
		<h1 class="font-bold text-6xl uppercase">Amin Osman</h1>
		<h2 class="italic text-6xl mt-2 uppercase">Portfolio</h2>
		<p class="mt-8">
			Zufall, Zufall, Zufall<br /> Klicke dich durch und lass den Zufall zu.<br /> Eine ausgewählte
			Sammlung von Bildern seit August 2022.<br /> Verschiedenste Bilder die alle etwas mit mir zu
			tun haben.<br /> Kombiniere und finde komische, lustige und interessante Zusammenhänge.<br /> Der
			Zufall bestimmt, deshalb musst du umso genauer hinschauen!
		</p>
	</div>
	<div class="flex-1 lg:mt-20  mx-auto overflow-y-hidden max-w-lg xl:max-w-3xl 3xl:max-w-5xl">
		<div class="flex items-center flex-col  ">
			<p class="font-light">refresh</p>
			<button
				class="{isIconRotated
					? 'rotate-180'
					: 'rotate-180'} p-4 mt-2 bg-gray-200 hover:bg-gray-300 transition-all rounded-full"
				on:click={getRandomImages}
				><img src="/images/pfeil.svg" alt="arrow" class="h-8 w-8 transition-all" /></button
			>
		</div>
		{#if imagesToDisplay.length}
			<div class="flex mt-8 gap-x-2 lg:p-0">
				<div>
					<img
						alt={imagesToDisplay[1].title}
						src={imagesToDisplay[1].url}
						class="max-w-full h-auto"
					/>
					<p>
						{imagesToDisplay[1].title},{imagesToDisplay[1].year},{imagesToDisplay[1]
							.material},{imagesToDisplay[1].mass}
					</p>
				</div>
				<!-- <div class="h-full border border-black hidden lg:visible" /> -->
				<div>
					<img
						alt={imagesToDisplay[0].title}
						src={imagesToDisplay[0].url}
						class="max-w-full h-auto"
					/>
					<p>
						{imagesToDisplay[0].title},{imagesToDisplay[0].year},{imagesToDisplay[0]
							.material},{imagesToDisplay[0].mass}
					</p>
				</div>

				<!-- <div class="flex-col flex justify-end">
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
					<p>
						{imagesToDisplay[1].title},{imagesToDisplay[1].year},{imagesToDisplay[1]
							.material},{imagesToDisplay[1].mass}
					</p>
				</div> -->
			</div>
		{/if}
	</div>
</div>

<!-- <div class="w-full flex flex-wrap items-center h-screen">
	<div class="p-8 max-w-lg">
		<h1 class="font-bold text-6xl uppercase">Amin Osman</h1>
		<h2 class="italic text-6xl mt-2 uppercase">Portfolio</h2>
		<p class="mt-8 ">
			Zufall, Zufall, Zufall Klicke dich durch und lass den Zufall zu. Eine ausgewählte Sammlung von
			Bildern seit August 2022. Verschiedenste Bilder die alle etwas mit mir zu tun haben.
			Kombiniere und finde komische, lustige und interessante Zusammenhänge. Der Zufall bestimmt,
			deshalb musst du umso genauer hinschauen!
		</p>
	</div>

	<div class="flex-1 flex justify-between flex-col xl:h-full py-2 lg:py-20">
		<div class="flex justify-center lg:mb-8">
			<div class="flex items-center flex-col">
				<p class="font-light">refresh</p>
				<button
					class="{isIconRotated
						? 'rotate-180'
						: 'rotate-180'} p-4 mt-2 bg-gray-200 hover:bg-gray-300 transition-all rounded-full"
					on:click={getRandomImages}
					><img src="/images/pfeil.svg" alt="arrow" class="h-8 w-8 transition-all" /></button
				>
			</div>
		</div>
		{#if imagesToDisplay.length}
			<div class="flex gap-x-4 min-h-[500px] overflow-hidden w-full justify-center xl:p-0 p-8">
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
</div> -->
