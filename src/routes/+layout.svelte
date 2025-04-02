<script lang="ts">
	import '../app.css';

	let { children } = $props();
	
	import { AppBar } from '@skeletonlabs/skeleton-svelte';
  	import Paperclip from '@lucide/svelte/icons/paperclip';
  	import Calendar from '@lucide/svelte/icons/calendar';
  	import CircleUser from '@lucide/svelte/icons/circle-user';
  	import Menu from '@lucide/svelte/icons/menu';

  	import { Navigation } from '@skeletonlabs/skeleton-svelte';
	
  // Icons
  	import IconFolder from '@lucide/svelte/icons/folder';
  	import IconImage from '@lucide/svelte/icons/image';
  	import IconMusic from '@lucide/svelte/icons/music';
  	import IconVideo from '@lucide/svelte/icons/video';

  // State
  let value = $state('files');

</script>



<div class="h-screen w-screen flex flex-col">
	<AppBar centerClasses="hidden sm:block">
		{#snippet lead()}
			
			<div class="block sm:hidden">
				<Menu size={20} />
			</div>
		{/snippet}
		{#snippet trail()}
				<Paperclip size={20} />
				<Calendar size={20} />
				<CircleUser size={20} />
		{/snippet}
		<span>Title</span>
	</AppBar>
  
	<div class="flex flex-1 h-full">
	<!-- Component -->
	<Navigation.Rail {value} onValueChange={(newValue) => (value = newValue)}>
	  {#snippet tiles()}
		<Navigation.Tile href="/" label="Home"><IconFolder /></Navigation.Tile>
		<Navigation.Tile href="/Artifact Data" label="Artifact Data"><IconImage /></Navigation.Tile>
		<Navigation.Tile id="music" label="Music"><IconMusic /></Navigation.Tile>
		<Navigation.Tile id="videos" label="Videos"><IconVideo /></Navigation.Tile>
	  {/snippet}
	</Navigation.Rail>
	<!-- Content -->
	{@render children()}
  </div>
</div>