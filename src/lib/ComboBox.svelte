<script lang="ts">
    export let placeholder: string = "Search...";
    export let options: string[];

    let isOpen: boolean = false;
</script>

<div class="flex flex-col m-3">
    <input
        class="border border-gray-200 focus:border-gray-300 transition duration-200 py-2 px-3 rounded-t-md focus:outline-none"
        type="text"
        on:click={() => isOpen = true}
        on:blur={() => isOpen = false}
        {placeholder}
    />
    {#if isOpen}
    <div class="border border-t-0 rounded-b-md border-gray-300">
        {#each options as option}
            <p class="py-2 px-3 odd:bg-neutral-50">{option}</p>
        {/each} 
    </div>
    {/if}
</div>
