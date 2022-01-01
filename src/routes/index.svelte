<script lang="ts">
    import { Drawer } from "$lib";

    let open = false;
</script>

<button type="checkbox" on:click={() => open = !open}>Toggle</button>

<Drawer bind:open>
    text
</Drawer>