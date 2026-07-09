<script>
    let { activeTitle, authors } = $props();
</script>

<div class="mb-4 flex flex-row justify-between items-start">
    <h1 class="cell-cell text-4xl">Cell</h1>
    <h2 class="cell-article text-3xl">Article</h2>
</div>
<h1 contenteditable="true" bind:innerText={activeTitle} 
class="text-4xl wrap-normal cell-title"></h1>