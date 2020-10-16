<script>
    import { onMount } from "svelte";
    import { slide} from "svelte/transition";
      import { quartInOut } from 'svelte/easing';
    import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();
    export let img = "image.svg"
    export let name = "Name"
    export let maybe = ""
    export let url = "/"
    let imx
    onMount(()=>{
        if(img == "image.svg")
            imx.style=`background: url('/${img}');    background-repeat: no-repeat;     background-size: 50% 50%;  background-position: center;`
        else
            imx.style=`background: url('/${img}');    background-repeat: no-repeat;     background-size:cover;  background-position: center;`
    })
    function handleClick(){
        maybe=name;
		dispatch('sub', {
			path: name
		});
    }
</script>

<div class="card" on:click={handleClick} >
    <div class="image" bind:this={imx} />
    <div class="row">
        <h3>
            {name}
        </h3>
       </div>
</div> 
{#if maybe==name}
    <div class="info" transition:slide={{duration:650,easing:quartInOut}} >
    
        <div class="imagebig" style={`background: url('/${img}');    background-repeat: no-repeat; background-size: ${img == 'image.svg' ? '50% 50%' : 'cover'};  background-position: center;`} />
      <div class="url"><a href={"https://"+url}>{url}</a></div>

        <slot name="desc"></slot>
    </div>
{/if}

<style>
h3{

    font-size: 1.8em;
    letter-spacing: 5px;
    font-family: 'Rajdhani', sans-serif;
  

    padding:5px;

    padding-left: 10px;
}
.info{
    position: absolute;
    width:100%;
height: calc(100% - 65px);
	background-color: rgba(0,0,0,.95);


    z-index: 5;
    top:65px;
    left:0px;
    color:white;
    overflow-x: hidden;
    overflow-y: auto;
}

.url{
padding: 20px;
    padding-top:30px;

    font-size: 1.5em;
    position: relative;

}
.url a{
 background-color: white;
padding: 5px;
padding-left:10px;
padding-right: 10px;
border-radius: 10px;
color:black;
}
.image{
    height: 200px;
    width: 100%;
    position: relative;
}
.imagebig{
max-width: 400px;
    width: calc(100% - 40px);
    height: 300px;
    position: relative;
    margin-top: 30px;
    margin-left: 20px;
    border: 2px solid white;
    border-radius: 25px;

}
.card{
    min-width:280px;
    margin:50px;
box-shadow: #00000082 0px 6px 11px 1px;
        overflow: hidden;
        border-radius: 15px;
        cursor: pointer;
        transition-duration: .4s;
}
.card:hover{
    transform: scale(1.1);
}
.row{
    position: relative;
    background-color: white;
    color:black;
            
}

</style>