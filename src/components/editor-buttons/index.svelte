<style type='text/sass'>
	@import './styles.sass'
</style>

<script lang="ts">
    import FaBold from 'svelte-icons/fa/FaBold.svelte';
    import FaItalic from 'svelte-icons/fa/FaItalic.svelte';
    import FaAlignLeft from 'svelte-icons/fa/FaAlignLeft.svelte';
    import FaAlignCenter from 'svelte-icons/fa/FaAlignCenter.svelte';
    import FaAlignRight from 'svelte-icons/fa/FaAlignRight.svelte';
    import FaAlignJustify from 'svelte-icons/fa/FaAlignJustify.svelte';
</script>

<div class="buttons-container">
    <button class="editor-button">
        <FaBold />
    </button>
    <button class="editor-button">
        <FaItalic />
    </button>
    
    <span class="divider"></span>

    <button class="editor-button">
        <FaAlignLeft />
    </button>
    <button class="editor-button">
        <FaAlignCenter />
    </button>
    <button class="editor-button">
        <FaAlignRight />
    </button>
    <button class="editor-button">
        <FaAlignJustify />
    </button>
</div>