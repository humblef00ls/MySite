<script>
import Typewriter from 'svelte-typewriter'
import {  fly} from "svelte/transition";
function log() {
    v = true
}
 export let v = false
</script>
<Typewriter cascade interval={60} cursor={false} on:done={log}>
    <h1>Hello World!</h1>
   <h1>I am Aparimeya</h1>

</Typewriter>


<style>
h1{
    font-size: 3rem;
    font-weight: 400;
}

</style>