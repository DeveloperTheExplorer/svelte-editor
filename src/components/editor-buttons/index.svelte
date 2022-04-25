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
    import type { EditType } from '@/interface/editor';

    export let handleButtonClick: (type: EditType) => void
    
    const handleClick = (type: EditType) => (_) => handleButtonClick(type)
</script>

<div class="buttons-container">
    <button class="editor-button" on:click={handleClick('bold')}>
        <FaBold />
    </button>
    <button class="editor-button" on:click={handleClick('italic')}>
        <FaItalic />
    </button>
    
    <span class="divider"></span>

    <button class="editor-button" on:click={handleClick('align-left')}>
        <FaAlignLeft />
    </button>
    <button class="editor-button" on:click={handleClick('align-center')}>
        <FaAlignCenter />
    </button>
    <button class="editor-button" on:click={handleClick('align-right')}>
        <FaAlignRight />
    </button>
    <button class="editor-button" on:click={handleClick('align-justify')}>
        <FaAlignJustify />
    </button>
</div>