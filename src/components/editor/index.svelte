<style type='text/sass' global>
@import './styles.sass'

:global(.bold)
    font-weight: bold

:global(.italic)
    font-style: italic

:global(.align-left)
    text-align: left

:global(.align-center)
    text-align: center

:global(.align-right)
    text-align: right

:global(.align-justify)
    text-align: justify
</style>

<script lang="ts">
    import type { EditType } from '../../interface/editor';
    import EditorButtons from '../editor-buttons/index.svelte'
    export let value: string;
    
    const handleParentNodeStyling = (parentElement: HTMLElement, type: EditType) => {
        const { classList } = parentElement;

        if (classList.contains(type)) {
            classList.remove(type);

            return;
        }

        if (type.includes('align')) {
            if (parentElement.tagName === 'SPAN') {
                return handleParentNodeStyling(parentElement.parentElement, type);
            }
            classList.forEach(
                (className) => {
                    if (className.includes('align')) {
                        classList.remove(className);
                    }
                }
            )
        }

        classList.add(type); 
    }

    const handleButtonClick = (type: EditType) => {
        const selection = window.getSelection();

        if (!selection) {
            return;
        }

        const { anchorNode, anchorOffset, focusOffset } = selection;
        const { textContent } = anchorNode;
        const parentElement = anchorNode.parentElement;
        const selectedText = textContent.substring(anchorOffset, focusOffset);
        const isParentNode = selectedText.length === 0 
            || type.includes('align') 
            || selectedText === parentElement.innerText;

        console.log('check: selection', selection);
        console.log('check: isParentNode', isParentNode);
        console.log('check: selectedText', selectedText);

        if (isParentNode) {
            handleParentNodeStyling(parentElement, type);

            return;
        }
        
        const contentSplit = parentElement.innerHTML.split(selectedText);
        const newElement = `<span class="${type}">${selectedText}</span>`;
        const editedContent = contentSplit[0] + newElement + contentSplit[1];

        parentElement.innerHTML = editedContent;
    }
    
</script>

<div class="container">
    <div class="editor-controller">
        <EditorButtons handleButtonClick={handleButtonClick} />
    </div>
    <div class="editor-main" contenteditable="true" bind:innerHTML={value}></div>
    <span class="italic">wtf</span>
</div>