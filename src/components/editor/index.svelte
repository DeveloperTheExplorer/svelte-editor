<style type='text/sass'>
	@import './styles.sass'
</style>

<script lang="ts">
    import EditorButtons from '@/components/editor-buttons/index.svelte'
    export let value: string;
</script>

<div class="container">
    <div class="editor-controller">
        <EditorButtons />
    </div>
    <div class="editor-main" contenteditable="true">
        {@html value}
    </div>
</div>