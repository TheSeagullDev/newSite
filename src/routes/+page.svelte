<script>
	import bgImg from '$lib/assets/bgImg.png';
	import { onMount } from 'svelte';

	let time = $state(new Date().toLocaleString());

	let screenHeight = $state();
	let screenWidth = $state();

	let welcomeWindow = $state();

	let welcomeLeft = $state();
	let welcomeTop = $state();
	onMount(() => {
		welcomeLeft = screenWidth / 2;
		welcomeTop = screenHeight / 2;
	});

	function updateClock() {
		time = new Date().toLocaleString();
	}

	let welcomeMoving = false;

	setInterval(updateClock, 1000);
</script>

<svelte:window
	bind:innerHeight={screenHeight}
	bind:innerWidth={screenWidth}
	onmousemove={(e) => {
		if (welcomeMoving) {
			welcomeLeft += e.movementX;
			welcomeTop += e.movementY;
			console.log(welcomeLeft, welcomeTop);
		}
	}}
	onmouseup={() => {
		welcomeMoving = false;
	}}
/>

<div style="background-image: url({bgImg});" class="h-screen items-center justify-center bg-cover">
	<div
		onmousedown={() => {
			welcomeMoving = true;
		}}
		class="absolute w-3/8 -translate-1/2 rounded-2xl border-2 p-4 pt-0 backdrop-blur-2xl"
		style="left: {welcomeLeft}px; top: {welcomeTop}px; user-select: none;"
	>
		<p class="w-full p-2 text-center">Welcome!</p>
		<div class="flex flex-col gap-2 rounded-xl bg-blue-100 p-12 shadow-2xl">
			<h1 class="text-3xl">Hi there! 👋</h1>
			<p class="text-md">
				I'm Noah, but you'll usually see me with the username TheSeagullDev. I'm a high school
				senior with a passion for coding, 3D printing, sound engineering, and more!
			</p>
		</div>
	</div>
</div>
<div
	class="fixed top-0 flex w-screen justify-between gap-16 bg-blue-100/5 p-2 text-blue-50 backdrop-blur-md"
>
	<div class="rounded-3xl bg-blue-900/20 p-2 px-4">TheSeagullDev</div>
	<div class="rounded-3xl bg-blue-900/20 p-2 px-4">Status: Applying to College 📝</div>
	<div class="rounded-3xl bg-blue-900/20 p-2 px-4">{time}</div>
</div>
