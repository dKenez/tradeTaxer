<script lang="ts">
	import { HeaderGlobalAction, Theme } from 'carbon-components-svelte';
	import { Carbon, Moon, Sun } from 'carbon-icons-svelte';
	import type { CarbonTheme } from 'carbon-components-svelte/types/Theme/Theme.svelte';

	function isLight(theme: CarbonTheme) {
		return ['white', 'g10', 'g80'].includes(theme);
	}

	function inter(theme: string) {
		return theme.substring(0, 2).toUpperCase();
	}

	const toggleTheme = () => {
		theme = theme === 'g90' ? 'white' : 'g90';
	};

	let theme: CarbonTheme = 'white';
	$: themeIcon = isLight(theme) ? Moon : Sun;
	$: funnyThem = theme + 'fg' + inter(theme);
</script>

<Theme bind:theme persist persistKey="__carbon-theme" />

<HeaderGlobalAction aria-label="NightMode" icon={themeIcon} on:click={toggleTheme} />
