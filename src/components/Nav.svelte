
<script>
let p = window.location.hash.substr(1) 
</script>
<nav>
			<a href="#about" class:active={p=="about"}> About </a>
            |
			<a href="#projects" class:active={p=="projects"} > Projects </a>
            |
			<a href="#contact" class:active={p=="contact"}> Contact </a>
</nav>
<style>
nav{
    position: absolute;
    bottom:20px;
    left:50%;
    transform: translate3d(-50%,0,0);
    width: 100%;
    text-align: center;
    font-size: 1.5em;

	font-weight: 500;
	font-family: 'Rajdhani', sans-serif;

    text-transform: uppercase;
    color:white;
}
a{
    	letter-spacing: .5vw;
    position: relative;
    overflow: hidden;
    color:white;
            z-index: 1;
                   transition-duration: .35s;
            padding:5px;
                	padding-left: calc(5px + .5vw);

}
a:hover{
    color: black;
}
a:hover::before{
            transform: translate3d(0,0px,0);
}
a::before{
		content: '';
		top:0px;
		left:0px;
		position: absolute;
		z-index: -1;
		height:100%;
		width:100%;
		background-color: white;
        transition-duration: .35s;
        transform: translate3d(0,100px,0);
}
a.active{
        color: black;
}
a.active::before{
                transform: translate3d(0,0px,0);
}
@media only screen and (max-width: 500px) {
        nav{
                 font-size: 1.1em
        }

    }
</style>