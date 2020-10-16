<script>
	import { slide } from 'svelte/transition';
    import { quintInOut } from 'svelte/easing';
        import Nav from './Nav.svelte'
    	function swipeRight(node, { duration }) {
		return {
			duration,
			css: t => {
				const eased = quintInOut(t);
				return `
                    transform: translate3d(${(1-eased)*100}%,0,0);
                    `
			}
		};
	}
</script>

    <div transition:swipeRight={{duration: 800 }}  class="panel">
        <a class="close" href="#home"> 
            <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.25" stroke-linecap="round" stroke-linejoin="round" class="feather feather-x"><line x1="18" y1="6" x2="6" y2="18"></line><line x1="6" y1="6" x2="18" y2="18"></line></svg>
        </a>
        <h2>Contact</h2>
        <article  >
            <a href="/resume.pdf" class="resume"> RESUME</a>
            <div class="icony">
                <a class="iconx" href="https://www.linkedin.com/in/aparimeya-taneja-1a7300162/">
                <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-linkedin"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"></path><rect x="2" y="9" width="4" height="12"></rect><circle cx="4" cy="4" r="2"></circle></svg>
                </a>
                <a class="iconx" href="https://www.instagram.com/aparimeya/">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-instagram"><rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line></svg>
                </a>
            </div>
            <div class="icony">
                <a class="iconx" href="mailto:aparimeya.taneja@duke.edu">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-mail"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path><polyline points="22,6 12,13 2,6"></polyline></svg>
                 </a>
                <a class="iconx" href="https://github.com/humblef00ls">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-github"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path></svg>
                </a>
            </div>
        </article>
        <Nav />
    </div>


<style>
    .close{
        left:0px;
    }
    .panel{
        top: 3vh;
        right:0px;
        height: 94vh;
        min-width: 330px;
        width: 600px;
        border-radius: 15px 0px 0px 15px;

    }
    h2{
        padding-right: 10px;
        flex-direction: row-reverse;
    }


    article{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
    height: calc(100% - 140px);
    }
    .iconx{
        height: 50px;
        width: 50px;
    }
    .icony{
display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    width: 100%;

    }
    .resume{
        font-size: 1.4em;
        font-family: 'Rajdhani', sans-serif;
        font-weight: 500;
        padding:8px;
        padding-left: 20px;
        padding-right: 12px;
        letter-spacing: 8px;
        border-radius: 5px;
        background-color: white;
        color:black;

    }
    .iconx svg {
        stroke: white;
        stroke-width: 1.3;
    }
    @media only screen and (max-width: 1000px) {
        .panel{
                 width: 500px;
        }
    }
    @media only screen and (max-width: 600px) {
        .panel{
                 width: 85vw;
        }
    }
</style>