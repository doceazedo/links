<script lang="ts">
	import { fade, fly } from "svelte/transition";
	import { quintOut } from "svelte/easing";
	import PlayCircleIcon from "$lib/icons/PlayCircleIcon.svelte";
	import BandcampIcon from "$lib/icons/BandcampIcon.svelte";
	import GitHubIcon from "$lib/icons/GitHubIcon.svelte";
	import InstagramIcon from "$lib/icons/InstagramIcon.svelte";
	import SoundCloudIcon from "$lib/icons/SoundCloudIcon.svelte";
	import TwitterIcon from "$lib/icons/TwitterIcon.svelte";
	import YouTubeIcon from "$lib/icons/YouTubeIcon.svelte";
	import LoveLetterEmoji from "$lib/icons/LoveLetterEmoji.svelte";
	import FileBoxEmoji from "$lib/icons/FileBoxEmoji.svelte";

	const socials = [
		{ icon: InstagramIcon, url: "https://instagram.com/doceazedo911" },
		{ icon: TwitterIcon, url: "https://twitter.com/doceazedo911" },
		{ icon: SoundCloudIcon, url: "https://soundcloud.com/doceazedo" },
		{ icon: YouTubeIcon, url: "https://www.youtube.com/@DoceAzedo" },
		{ icon: BandcampIcon, url: "https://doceazedo.bandcamp.com" },
		{ icon: GitHubIcon, url: "https://github.com/doceazedo" },
	];

	let showEmail = false;
	let emailInput: HTMLInputElement;
	let copyEmailLabel = "Copiar";
	const copyEmail = () => {
		emailInput.select();
		emailInput.setSelectionRange(0, 99999);
		navigator.clipboard.writeText(emailInput.value);
		if (copyEmailLabel === "Copiar") {
			copyEmailLabel = "Copiado!";
			setTimeout(() => (showEmail = false), 250);
			setTimeout(() => (copyEmailLabel = "Copiar"), 500);
		}
	};
</script>

<div class="mx-auto flex w-full max-w-[32rem] flex-col items-center gap-6 p-6">
	<img src="/logo.png" class="h-11 w-auto" alt="Logo DoceAzedo" />

	<div class="flex gap-3">
		{#each socials as social}
			<a
				href={social.url}
				class="flex size-10 items-center justify-center rounded-md bg-white/5 transition-all hover:-translate-y-0.5"
			>
				<svelte:component this={social.icon} size={20} />
			</a>
		{/each}
	</div>

	<div class="flex w-full flex-col gap-3">
		<a
			href="https://www.youtube.com/watch?v=4r81BjzM7bM"
			class="flex w-full flex-col gap-2 rounded-xl bg-white/5 p-2 transition-all hover:-translate-y-0.5"
		>
			<figure
				class="flex aspect-video w-full items-center justify-center rounded-md bg-[url(/lhamaday-thumbnail.webp)] bg-cover text-white/75"
			>
				<PlayCircleIcon />
			</figure>
			<div class="flex items-center gap-2">
				<span
					class="flex size-8 items-center justify-center rounded-md bg-[#FF0000]"
				>
					<YouTubeIcon size={20} />
				</span>
				<div>
					<p class="text-sm font-medium">[DJ Set] Live @ LhamaDay 2024</p>
					<p class="text-xs opacity-80">Assistir no YouTube</p>
				</div>
			</div>
		</a>

		<a
			href="https://soundcloud.com/doceazedo/lhamaday-2024"
			class="flex items-center gap-2 rounded-lg bg-[#FF5500] p-2 transition-all hover:-translate-y-0.5"
		>
			<span class="flex size-8 items-center justify-center">
				<SoundCloudIcon />
			</span>
			<div>
				<p class="text-sm font-medium">[DJ Set] Live @ LhamaDay 2024</p>
				<p class="text-xs opacity-80">Ouvir no SoundCloud</p>
			</div>
		</a>

		<button
			on:click={() => (showEmail = true)}
			class="flex items-center gap-2 rounded-lg bg-white/5 p-2 text-sm font-medium transition-all hover:-translate-y-0.5"
		>
			<span class="flex size-8 items-center justify-center">
				<LoveLetterEmoji />
			</span>
			<p>E-mail para contato/booking</p>
		</button>

		{#if showEmail}
			<div
				class="fixed left-0 top-0 flex h-full w-full flex-col items-center bg-black/80"
				in:fade={{ duration: 300, easing: quintOut }}
				out:fade={{ delay: 100, duration: 300, easing: quintOut }}
			>
				<button
					class="w-full flex-grow cursor-default"
					on:click={() => (showEmail = false)}
				/>
				<div
					class="flex w-full max-w-[50rem] flex-col gap-3 rounded-t-2xl bg-slate-50 p-6 text-slate-950"
					transition:fly={{
						duration: 300,
						y: 64,
						easing: quintOut,
					}}
				>
					<p class="font-medium">💌 E-mail para contato/booking:</p>
					<input
						readonly
						bind:this={emailInput}
						value="mgmt@doceazedo.com"
						class="rounded-md bg-slate-200 p-3 ring-blue-500"
					/>
					<button
						on:click={copyEmail}
						class="rounded-md border p-2.5 text-blue-500"
					>
						{copyEmailLabel}
					</button>
					<button
						on:click={() => (showEmail = false)}
						class="rounded-md border p-2.5 text-red-500"
					>
						Cancelar
					</button>
				</div>
			</div>
		{/if}

		<a
			href="https://go.doceazedo.com/presskit"
			class="flex items-center gap-2 rounded-lg bg-white/5 p-2 text-sm font-medium transition-all hover:-translate-y-0.5"
		>
			<span class="flex size-8 items-center justify-center">
				<FileBoxEmoji />
			</span>
			<p>Press kit</p>
		</a>
	</div>
</div>
