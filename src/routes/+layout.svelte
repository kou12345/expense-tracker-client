<script lang="ts">
	import '../app.postcss';
	import { AppShell, AppBar } from '@skeletonlabs/skeleton';
	import Navigation from '$lib/Navigation/Navigation.svelte';
	import Footer from '$lib/Footer.svelte';
	import { initializeStores, Drawer, getDrawerStore } from '@skeletonlabs/skeleton';

	// これはSkeletonのDrawer、Modal、Toastストアを実装する際に一度だけ必要で、SvelteKit SSRの既知の問題を防ぐことができます。
	initializeStores();
	const drawerStore = getDrawerStore();

	function drawerOpen(): void {
		drawerStore.open({});
	}
</script>

<Drawer>
	<Navigation />
</Drawer>
<!-- サイドバーのベース幅はw-0（ゼロ）。ウィンドウが大きなブレイクポイントに達するとw-64（256px）に拡張される。 -->
<!-- svelte-ignore missing-declaration -->
<AppShell slotSidebarLeft="bg-surface-500/5 w-0 lg:w-64">
	<!-- header -->
	<svelte:fragment slot="header">
		<AppBar gridColumns="grid-cols-3" slotDefault="place-self-center" slotTrail="place-content-end">
			<svelte:fragment slot="lead">
				<div class="flex items-center">
					<button class="lg:hidden btn btn-sm mr-4" on:click={drawerOpen}>
						<span>
							<svg viewBox="0 0 100 80" class="fill-token w-4 h-4">
								<rect width="100" height="20" />
								<rect y="30" width="100" height="20" />
								<rect y="60" width="100" height="20" />
							</svg>
						</span>
					</button>
					<strong class="text-xl uppercase">Skeleton</strong>
				</div>
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>
	<!-- footer -->
	<svelte:fragment slot="footer">
		<Footer />
	</svelte:fragment>
	<!-- sidebar -->
	<svelte:fragment slot="sidebarLeft">
		<Navigation />
	</svelte:fragment>
	<!-- Page Route Content -->
	<slot />
</AppShell>
