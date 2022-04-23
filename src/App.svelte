<style type='text/sass'>
	@import './styles/main.sass'
</style>

<script lang="ts">
	import Editor from './components/editor/index.svelte'
    import { html } from './data/sample'
	export let name: string;
</script>

<main>
	<h1>Welcome to Arvini's Editor</h1>
	<Editor value={html} />
</main>