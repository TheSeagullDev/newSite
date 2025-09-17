<script>
	import bgImg from '$lib/assets/bgImg.png';

	let time = $state(new Date().toLocaleString());

	function updateClock() {
		time = new Date().toLocaleString();
	}

	function dragElement(element) {
		let initialX = 0;
		let initialY = 0;
		let currentX = 0;
		let currentY = 0;

		function startDragging(e) {
			e = e || window.event;
			e.preventDefault();

			initialX = e.clientX;
			initialY = e.clientY;
		}

		function elementDrag(e) {
			e = e || window.event;
			e.preventDefault();

			currentX = initialX - e.clientX;
			currentY = initialY - e.clientY;

			initialX = e.clientX;
			initialY = e.clientY;
		}
	}

	setInterval(updateClock, 1000);
</script>

<div style="background-image: url({bgImg});" class="h-screen items-center justify-center bg-cover">
	<div
		class="absolute top-1/2 left-1/2 w-3/8 -translate-1/2 rounded-2xl border-2 p-6 px-4 pt-16 backdrop-blur-2xl"
	>
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
	<div class="rounded-3xl bg-blue-900/20 p-2 px-4">Applying to College 📝</div>
	<div class="rounded-3xl bg-blue-900/20 p-2 px-4">{time}</div>
</div>
