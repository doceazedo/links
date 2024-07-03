<script lang="ts">
	import PlayCircleIcon from "$lib/icons/PlayCircleIcon.svelte";
	import BandcampIcon from "$lib/icons/BandcampIcon.svelte";
	import GitHubIcon from "$lib/icons/GitHubIcon.svelte";
	import InstagramIcon from "$lib/icons/InstagramIcon.svelte";
	import SoundCloudIcon from "$lib/icons/SoundCloudIcon.svelte";
	import TwitterIcon from "$lib/icons/TwitterIcon.svelte";
	import YouTubeIcon from "$lib/icons/YouTubeIcon.svelte";

	const socials = [
		{ icon: InstagramIcon, url: "https://instagram.com/doceazedo911" },
		{ icon: TwitterIcon, url: "https://twitter.com/doceazedo911" },
		{ icon: SoundCloudIcon, url: "https://soundcloud.com/doceazedo" },
		{ icon: YouTubeIcon, url: "https://www.youtube.com/@DoceAzedo" },
		{ icon: BandcampIcon, url: "https://doceazedo.bandcamp.com" },
		{ icon: GitHubIcon, url: "https://github.com/doceazedo" },
	];
</script>

<div class="mx-auto flex w-full max-w-[32rem] flex-col items-center gap-6 p-6">
	<img src="/logo.png" class="h-11 w-auto" alt="Logo DoceAzedo" />

	<div class="flex gap-1.5">
		{#each socials as social}
			<a
				href="/"
				class="flex size-8 items-center justify-center rounded-md bg-white/5 transition-all hover:-translate-y-0.5"
			>
				<svelte:component this={social.icon} size={16} />
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
	</div>
</div>
