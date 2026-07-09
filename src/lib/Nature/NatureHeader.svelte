<script>
    import NatureBreadcrumbs from "./NatureBreadcrumbs.svelte";
    let { activeTitle, authors } = $props();

    const todaysDate = new Date().toLocaleDateString('en-GB', {
        day: 'numeric',
        month: 'long',
        year: 'numeric'
    });

</script>

<span class="mb-6"><NatureBreadcrumbs/></span>
<span class="flex flex-row gap-2 mb-1">
    <h4>Article</h4><div class="nature-divider"/>
    <h4 class="nature-oa">Open access</h4><div class="nature-divider"/>
    <h4>Published: {todaysDate}</h4>
</span>
<h1 contenteditable="true" bind:innerText={activeTitle} 
class="text-4xl wrap-normal nature-title"></h1>
<span class="mt-6 wrap-normal flex flex-row gap-2">
 {#each authors as author, i}
    <h3 contenteditable="true" class="nature-author text-lg author">{author}</h3>
 {/each}
</span>

<style>
    .author::after{
        content: ', '
    }
    .author:last-of-type::after {
        content: ''
    }
</style>