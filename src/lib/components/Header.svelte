<script>
	import { PrismicLink } from '@prismicio/svelte';
	import WordMark from './WordMark.svelte';
	import ButtonLink from './ButtonLink.svelte';

	/** @type {import("@prismicio/client").Content.SettingsDocument}*/
	export let settings;

	console.log('Settings data:', settings);
</script>

<header>
	<nav
		class="flex flex-col items-center justify-between gap-6 border-t border-gray-600 px-8 py-7 md:flex-row"
		aria-label="main"
	>
		<a href="/">
			<WordMark />
			<span class="sr-only">{settings.data?.slices[0]?.primary.site_title}</span>
		</a>

		<ul class="flex gap-6">
			{#each settings.data?.slices[0]?.primary.navigation ?? [] as item (item.label)}
				<li>
					{#if item.cta_button}
						<ButtonLink field={item.link}>
							{item.label}
						</ButtonLink>
					{:else}
						<PrismicLink class="inline-flex min-h-11 items-center" field={item.link}
							>{item.label}</PrismicLink
						>
					{/if}
				</li>
			{/each}
		</ul>
	</nav>
</header>
