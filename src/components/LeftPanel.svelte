<script>
	import { slide } from 'svelte/transition';
    import { quintInOut } from 'svelte/easing';
    import Nav from './Nav.svelte'
    
    	function swipeLeft(node, { duration }) {
		return {
			duration,
			css: t => {
				const eased = quintInOut(t);
				return `
                    transform: translate3d(-${(1-eased)*100}%,0,0);
                    `
			}
		};
	}
</script>

    <div transition:swipeLeft={{duration: 800 }}  class="panel">
        <a class="close" href="#home"> 
            <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.25" stroke-linecap="round" stroke-linejoin="round" class="feather feather-x"><line x1="18" y1="6" x2="6" y2="18"></line><line x1="6" y1="6" x2="18" y2="18"></line></svg>
        </a>
        <h2>About</h2>
        <article >
        <div  class="pp"></div>
            <p>Hi! I am Aparimeya Taneja. I am a junior at Duke University and am majoring in Computer Science!</p>
            <p> I love space, dogs, art (<a href="https://www.instagram.com/humblef00ls/"> @humblef00ls</a>), gaming, and most of all creating things! </p>
            <p>Check out all of my projects and works <a href="#projects">here</a>, and feel free to reach out <a href="#contact"> here</a>! </p>
            <p>My goal is to be able to empower as many people as possible with technology. 
            So far I've created many beauitful UIs as well as functional web apps, but I strive to always learn new things. </p>
            <p>
            My most recent large project <a href="https://stockhub.app/">StockHub</a> is a culmination of everything I've learnt so far, and is powered by 
            cutting edge technologies like Svelte (also used in this website!), Serverless Cloud (GCP), NLP, etc. It is a US stock market analysis tool,
            and aims to help retail investors by providing them with free data about social metrics and options volume, as well as query this data
            market wide.        </p>
        </article>
        <Nav />
    </div>



<style>
    .close{
        right:0px;

    }
    .pp{
        height: 200px;
        width: 200px;
        border-radius: 50%;
  margin-bottom: 10px;
margin-top:20px;
    margin-left: auto;
    margin-right: auto;

        background-image: url("/levi.jpg");
        background-position: center;
        background-size: cover;
    }
    .panel{
        top: 3vh;
        height: 94vh;
        min-width: 350px;
        width: 60vw;
        border-radius: 0px 15px 15px 0px;
    }
    h2{
        
        padding-left: calc(1vw + 10px);

        flex-direction: row;

    }
 
    a{
        text-decoration: underline
    }
    @media only screen and (max-width: 1000px) {
        .panel{
                 width: 75vw;
        }
    }
    @media only screen and (max-width: 750px) {
        .panel{
                 width: 85vw;
        }

    }
</style>