<script lang="ts">
	import { HeaderGlobalAction, Theme } from 'carbon-components-svelte';
	import { Moon, Sun } from 'carbon-icons-svelte';
	import type { CarbonTheme } from 'carbon-components-svelte/types/Theme/Theme.svelte';

	function isLight(theme: CarbonTheme) {
		return ['white', 'g10', 'g80'].includes(theme);
	}

	function inter(theme: string) {
		return theme.substring(0, 2).toUpperCase();
	}

	function toggleTheme() {
		theme = theme === darkTheme ? lightTheme : darkTheme;
	}

	const darkTheme = 'g90';
	const lightTheme = 'white';

	let theme: CarbonTheme = 'white';
	$: themeIcon = isLight(theme) ? Moon : Sun;
</script>

<Theme bind:theme persist persistKey="__carbon-theme" />

<HeaderGlobalAction aria-label="NightMode" icon={themeIcon} on:click={toggleTheme} />
