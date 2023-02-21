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

<div class="block lg:flex">
	<div class="lg:p-8 p-2 xl:w-1/3 max-w-lg">
		<h1 class="font-bold text-3xl lg:text-6xl uppercase">Amin Osman</h1>
		<h2 class="italic text-3xl lg:text-6xl mt-2 uppercase">Portfolio</h2>
		<p class="mt-8 text-xs lg:text-md">
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
				class="p-4 mt-2 bg-gray-200 hover:bg-gray-300 transition-all rounded-full"
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
			</div>
		{/if}
	</div>
</div>
<div class="flex gap-x-2 absolute bottom-5 left-5">
	<a href="https://vimeo.com/user183795255" target="_blank" rel="noreferrer">
		<img
			alt="vimeo"
			class="h-5 w-5 cursor-pointer rounded-lg grayscale hover:grayscale-0"
			src="/icons/vimeo_icon_blue_on_white_rounded.jpg"
		/>
	</a>
	<a href="https://www.instagram.com/amin.o.17/" target="_blank" rel="noreferrer">
		<img
			alt="instagram"
			class="h-5 w-5 cursor-pointer filter grayscale hover:grayscale-0"
			src="/icons/instagram.png"
		/>
	</a>
</div>
