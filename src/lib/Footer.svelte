<script>
	import { page } from '$app/stores';
	import { TabAnchor, TabGroup } from '@skeletonlabs/skeleton';
	import Home from './Icon/Home.svelte';
</script>

<TabGroup
	justify="justify-center"
	active="variant-filled-primary"
	hover="hover:variant-soft-primary"
	flex="flex-1 lg:flex-none"
	rounded=""
	border=""
	class="bg-surface-100-500-token w-full"
>
	<TabAnchor href="/" selected={$page.url.pathname === '/'}>
		<svelte:fragment slot="lead">
			<Home />
		</svelte:fragment>
	</TabAnchor>
	<TabAnchor href="/" selected={$page.url.pathname === '/about'}>
		<svelte:fragment slot="lead">
			<button type="button" class="btn-icon btn-icon-xl variant-filled">+</button>
		</svelte:fragment>
	</TabAnchor>
	<TabAnchor href="/" selected={$page.url.pathname === '/'}>
		<svelte:fragment slot="lead">
			<Home />
		</svelte:fragment>
	</TabAnchor>
</TabGroup>
