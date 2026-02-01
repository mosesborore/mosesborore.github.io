<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';
  import {base} from '$app/paths';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
  <link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Manrope:wght@200..800&display=swap" rel="stylesheet">
</svelte:head>

<div class="fixed top-0 z-99999 w-full">
	<nav class="mt-4 flex items-center justify-center">
		<div
			class="flex items-center justify-between rounded-2xl
             border border-white/20 bg-white/20 px-2 text-base-content/90 shadow-lg backdrop-blur-md"
		>
			<ul class="m-2 flex items-center space-x-8 text-sm prose-a:hover:text-white">
				<li><a href="{base}/">Home</a></li>
				<li><a href="#skills">Skills</a></li>
				<li><a href="#projects">Projects</a></li>
			</ul>
		</div>
	</nav>
</div>

{@render children()}
