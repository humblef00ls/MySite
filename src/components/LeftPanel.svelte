<script>
import {  fly} from "svelte/transition";
export let v;
</script>

{#if v}
    <div in:fly={{duration:500,x:-30}} class="leftpanel">
    sd
    </div>
{/if}

<style>
.leftpanel{
    margin-top: 30px;
    font-size: 2rem;
        font-weight: 300;
}
</style>