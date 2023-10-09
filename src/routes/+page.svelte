<script lang="ts">
	import Player from '@vimeo/player';

	let vimeoDiv: HTMLDivElement;
	let vimeoPlayer: Player;
	let videoHasLoaded: boolean = false;

	let vimeoId: string = '';

	const reloadPlayer = async () => {
		if (vimeoDiv == null || vimeoId === '') {
			return;
		}

		// if player is already loaded, destroy and load it again
		if (vimeoPlayer != null) {
			await vimeoPlayer.destroy();
			videoHasLoaded = false;
		}

		try {
			const vimeoOptions: any = {
				responsive: true,
				color: '9358fa',
				title: false
			};

			// if it starts with https then we set on url, not on id
			if (vimeoId.startsWith('https://')) {
				vimeoOptions.url = vimeoId;
			} else {
				vimeoOptions.id = vimeoId;
			}

			vimeoPlayer = new Player(vimeoDiv, vimeoOptions);

			vimeoPlayer.on('loaded', (event: any) => {
				console.log('============= loaded', JSON.stringify(event));
				videoHasLoaded = true;
			});

			vimeoPlayer.on('error', (event: any) => {
				console.log('============= error', JSON.stringify(event));
				videoHasLoaded = true;
			});

			vimeoPlayer.on('timeupdate', (event: any) => {
				console.log('============= timeupdate', JSON.stringify(event));
			});

			vimeoPlayer.on('seeked', (event: any) => {
				console.log('============= seeked', JSON.stringify(event));
			});

			vimeoPlayer.on('play', (event: any) => {
				console.log('============= play', JSON.stringify(event));
			});

			vimeoPlayer.on('pause', (event: any) => {
				console.log('============= pause', JSON.stringify(event));
			});
		} catch (error) {
			console.error('========= error 2', JSON.stringify(error));
		}
	};
</script>

<main class="w-full max-w-screen-lg px-3 md:px-0 mx-auto mt-3 md:mt-5">
	<h1 class="font-bold text-xl">Vimeo Player iOS Issue</h1>

	<p class="text-slate-500 my-3">Add the vimeo ID or URL below:</p>

	<fielset
		class="inline-flex flex-col w-full md:flex-row space-x-0 md:space-y-0 space-y-3 items-center md:space-x-3 mb-3"
	>
		<input type="text" bind:value={vimeoId} class="rounded-lg w-full md:w-auto" />
		<button
			on:click={reloadPlayer}
			disabled={vimeoId === ''}
			class="bg-emerald-600 w-full md:w-auto active:bg-emerald-700 transition-all disabled:pointer-events-none disabled:cursor-not-allowed disabled:bg-emerald-600/50 text-white rounded-lg font-bold p-2"
		>
			Reload player
		</button>
	</fielset>

	<div
		bind:this={vimeoDiv}
		class="{!videoHasLoaded
			? 'h-44 animate-pulse rounded-lg bg-slate-200 md:h-96'
			: ''} w-full max-w-full"
	/>
</main>
