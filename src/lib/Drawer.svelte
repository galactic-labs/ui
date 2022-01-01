<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	import { slide, fade } from 'svelte/transition';

	export let open: boolean;
	export let callback: () => void = () => {};

	const dispatch = createEventDispatcher();

	$: dispatch(open ? 'open' : 'close');

	function mountDrawer(node: HTMLElement, { target }) {
		if (target) target.appendChild(node);
		node.focus();
	}
</script>

{#if open}
	<div
		class="fixed flex items-end top-0 w-full h-full bg-black/50"
		on:click|self={() => {
			open = false;
			callback();
		}}
		use:mountDrawer={{ target: document.body }}
		transition:fade={{ duration: 300 }}
	>
		<div
			class="rounded-t-md flex flex-col relative w-full bg-white border-t-gray-900/80"
			transition:slide={{ duration: 300 }}
			{...$$restProps}
		>
			<slot />
		</div>
	</div>
{/if}
