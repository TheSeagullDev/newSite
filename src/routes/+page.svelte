<script>
	import bgImg from '$lib/assets/bgImg.png';

    let time = $state(new Date().toLocaleString());

    function updateClock() {
        time = new Date().toLocaleString();
    }

    setInterval(updateClock, 1000);
</script>

<div
	style="background-image: url({bgImg});"
	class="flex h-screen items-center justify-center bg-cover"
>
	<div class="flex w-1/3 flex-col gap-2 rounded-xl border-2 bg-blue-100 p-12 shadow-2xl">
		<h1 class="text-3xl">Hi there! 👋</h1>
		<p class="text-md">
			I'm Noah, but you'll usually see me with the username TheSeagullDev. I'm a high school senior
			with a passion for coding, 3D printing, sound engineering, and more!
		</p>
	</div>
</div>
<div class="fixed top-0 flex w-screen bg-blue-100/5 backdrop-blur-md p-2 justify-between gap-16 text-blue-50">
	<div class="p-2 px-4 bg-blue-900/20 rounded-3xl">TheSeagullDev</div>
	<div class="p-2 px-4 bg-blue-900/20 rounded-3xl">Applying to College 📝</div>
	<div class="p-2 px-4 bg-blue-900/20 rounded-3xl">{time}</div>
</div>
