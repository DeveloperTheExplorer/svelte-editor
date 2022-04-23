<style type='text/sass'>
	@import './styles.sass'
</style>

<script lang="ts">
    import type { EditType } from '../../interface/editor';
    import EditorButtons from '../editor-buttons/index.svelte'
    export let value: string;

    const editTypeMapping = {
        bold: ['<strong>', '</strong>'],
        italic: ['<em>', '</em>'],
        'justify-left': ['<span style="text-align: left">', '</span>'],
        'justify-center': ['<span style="text-align: center">', '</span>'],
        justify: ['<span style="text-align: justify">', '</span>'],
    }

    const handleButtonClick = (type: EditType) => {
        const selection = window.getSelection();

        if (!selection) {
            return;
        }

        const styling = editTypeMapping[type];
        const textStart = selection.anchorOffset;
        const textEnd = selection.focusOffset;
        const selectedParagraph = selection.focusNode.data;
        const selectedText = selectedParagraph.substring(textStart, textEnd);
        const selectedSplit = value.split(selectedParagraph);
        const paragraphStart = selectedParagraph.substring(0, textStart);
        const paragraphEnd = selectedParagraph.substring(textEnd);
        const editedText = styling[0] + selectedText + styling[1];
        const editedParagraph = paragraphStart + editedText + paragraphEnd;
        const finalHTML = selectedSplit[0] + editedParagraph + selectedSplit[1];

        console.log('check: text', window.getSelection());
        console.log('check: text', selectedSplit);
        console.log('check: selectedText', selectedText)
        value = finalHTML;
    }
    
</script>

<div class="container">
    <div class="editor-controller">
        <EditorButtons handleButtonClick={handleButtonClick} />
    </div>
    <div class="editor-main" contenteditable="true">
        {@html value}
    </div>
</div>