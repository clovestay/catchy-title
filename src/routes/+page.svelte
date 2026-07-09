<script>
    import CellHeader from "$lib/Cell/CellHeader.svelte";
    import NatureBreadcrumbs from "$lib/Nature/NatureBreadcrumbs.svelte";
    import NatureHeader from "$lib/Nature/NatureHeader.svelte";

    const defaultTitle = "An inventive title: just around the corner"
    const defaultStyle = "Nature"

    const availableStyles = ["Nature", "Cell", "Science"]
    const unimplementedStyles = ["Science"]

    let activeTitle = $state(defaultTitle);
    let activeStyle = $state(defaultStyle);

    const authors = [
        "Bugs Bunny",
        "Daffy Duck",
        "Curious George",
        "Hungry Caterpillar"
    ]

    const updateTitle = (x) => {
        activeTitle = x.target?.value
        if(activeTitle == "") {
            activeTitle = defaultTitle
        }
    }

    const updateStyle = (x) => {
        activeStyle = x.target?.value
        if(!(activeStyle in availableStyles)) {
            activeStyle = defaultStyle
        }
    }

</script>

<div class="h-[300px] w-[70%] min-w-[70%] max-w-[700px]">
    {#if activeStyle === "Nature"}
        <NatureHeader activeTitle={activeTitle} authors={authors} />
    {:else if activeStyle === "Cell"}
        <CellHeader activeTitle={activeTitle} authors={authors} />
    {:else if activeStyle === "Science"}
        <span>Not implemented!</span>
    {:else}
        <span>Unknown style!</span>
    {/if}
</div>


<div class="flex flex-col gap-5 align-middle items-center w-[50%] max-w-[400px]">
    <input type="text" placeholder="Enter your title..." on:input={(x) => updateTitle(x)}
        class="border-gray-200 bg-gray-50 text-gray-800 p-2 w-[100%] rounded-sm"/>
    <select bind:value={activeStyle}>
        {#each availableStyles as journalStyle}
            <option value={journalStyle} disabled={journalStyle.includes(unimplementedStyles)}>{journalStyle}</option>
        {/each}
    </select>
</div>




