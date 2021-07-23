<script>
    import { onMount } from "svelte";
    let cx;
    let ctx;
    let w,h;
    let dpr
    let stop
    let dots =[]
    const scl = 40
    let maxwell
    let resh 
    let resw 
            let c = 0;
            let f = true
    function init(){
        dots=[]
        ctx = cx.getContext('2d')
        dpr = window.devicePixelRatio || 1;
        console.log(dpr)
        maxwell = Math.max(h,w) * 1.5
        resh = h * dpr + h/4
        resw = w * dpr + w/4
        if(resh > resw) 
        resw = resh
        else
        resh=resw
        ctx.scale(dpr,dpr);
         let max = Math.max(resw,resh) + 160
        for(let i = 0 ; i < max ; i++){
            let x =  max * Math.random()  ;
            let y =  max * Math.random()  ;
            let s =  Math.random() + .5 ;

            let dot = {

                x,
                y,
                s
            }
            dots = [...dots,dot]
        }

        setTimeout(draw,0);
        if(stop) 
        clearInterval(stop)
       stop = setInterval(()=>{
            c+=.1
        if(f)  cx.style=`transform:translate3d(-50%,-50%,0) rotate(${c}deg) ;  height:${maxwell}px`
        else{
   cx.style=`transform:translate3d(calc(-50% + ${(m.x)}px ),calc(-50% + ${(m.y)}px),0) rotate(${c}deg); height:${maxwell}px`
   
        }
        },40)
     
    }
    onMount(init)
    function draw(){

        ctx.clearRect(0,0,w,h)
        for (let d = 0;d<dots.length;d++) {  
            drawDot(dots[d].x,dots[d].y,dots[d].s,'white')
            if(probability(.4)){
                let min = Infinity
                let im = -1
                for (let dd = 0;dd<dots.length;dd++) {  
                    let xd = Math.abs( dots[dd].x -dots[d].x)
                    let yd = Math.abs( dots[dd].y -dots[d].y)
                    if(xd +yd > 0 && xd+yd < min){
                        min = xd+yd;
                        im = dd;

                    }
                }
            //console.log(dots[im],dots[d])
            ctx.beginPath();
            ctx.strokeStyle='rgba(255,255,255,0.3)'
            ctx.lineWidth = 1 ;
            ctx.moveTo(dots[d].x, dots[d].y);
            ctx.lineTo(dots[im].x, dots[im].y);
            ctx.stroke();
            }

        }
          
       
    }
    function drawDot(x, y, radius,color) {
    
 ctx.beginPath();
    ctx.arc(x, y, radius, 0, 2 * Math.PI);
    ctx.fillStyle =  color;
    ctx.fill();
}
var probability = function(n) {
    return !!n && Math.random() <= n;
};
	let m = { x: 0, y: 0 };
function parallax(event){
    f = false;
        m.x = (event.clientX - w/2)/15;
        m.y = (event.clientY - h/2)/15;

    cx.style=`transform:translate3d(calc(-50% + ${(m.x)}px ),calc(-50% + ${(m.y)}px),0) rotate(${c}deg);  height:${maxwell}px`
}
</script>
<svelte:window bind:innerWidth={w} bind:innerHeight={h} on:mousemove={parallax} />
<canvas bind:this={cx} height={resh} width={resw} style={`transform:translate3d(-50%,-50%,0);  height:${maxwell}px`} >

</canvas>

<style>
    canvas{
        position: fixed;
        z-index: 0;
        left:50%;
        top:50% ;
        animation: fader 3s forwards ease-in;
        opacity: 0;

    }
    @keyframes fader{
        to{
            opacity:.8
        }
    }

</style>
