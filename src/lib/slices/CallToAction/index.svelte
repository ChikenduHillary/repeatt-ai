<script lang="ts">
	import Bounded from '$lib/components/Bounded.svelte';
	import type { Content } from '@prismicio/client';
	import { PrismicText, type SliceComponentProps } from '@prismicio/svelte';
	import PlainLogo from './PlainLogo.svelte';
	import ButtonLink from '$lib/components/ButtonLink.svelte';

	type Props = SliceComponentProps<Content.CallToActionSlice>;

	const { slice }: Props = $props();
</script>

<Bounded
	data-slice-type={slice.slice_type}
	data-slice-variation={slice.variation}
	class="relative py-32 text-center font-medium md:py-40"
>
	<div
		class="glow absolute -z-10 aspect-square w-full max-w-sm rounded-full bg-violet-500/50 blur-[160px] filter"
	></div>
	<div
		class="glass-container rounded-lg bg-gradient-to-b from-gray-800 to-gray-900 p-4 md:rounded-xl"
	>
		<PlainLogo />
	</div>

	<h2 class="mt-8 max-w-xl text-5xl text-balance">
		<PrismicText field={slice.primary.heading} />
	</h2>

	{#if slice.primary.button_link}
		<ButtonLink field={slice.primary.button_link} class="mt-6">
			{slice.primary.button_label || 'Learn More'}
		</ButtonLink>
	{/if}
</Bounded>
