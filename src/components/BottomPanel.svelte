<script>
	import { slide } from 'svelte/transition';
    import { quintInOut } from 'svelte/easing';
    import Nav from './Nav.svelte'
    import Card from './Card.svelte'
    let subp = ""
    	function swipeUp(node, { duration }) {
		return {
			duration,
			css: t => {
				const eased = quintInOut(t);
				return `
                    transform: translate3d(0,${(1-eased)*100}%,0);
                    `
			}
		};
    }
    function handleSub(event){
        subp = event.detail.path
    }
    function handleSubClose(){
        subp = ""
    }
</script>

    <div transition:swipeUp={{duration: 800 }}   class="panel">
        <a class="close" href="#home" > 
            <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.25" stroke-linecap="round" stroke-linejoin="round" class="feather feather-x"><line x1="18" y1="6" x2="6" y2="18"></line><line x1="6" y1="6" x2="18" y2="18"></line></svg>
        </a>
        {#if subp != ""}
        <a class="close c2" href="#projects" on:click={handleSubClose}> 
           <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.25" stroke-linecap="round" stroke-linejoin="round" class="feather feather-chevron-left"><polyline points="15 18 9 12 15 6"></polyline></svg> </a>
        {/if}
        <h2>Projects{#if subp != ""}/{subp}{/if}</h2>
        <article >
           
                <Card name={"StockHub"} img={"stockhub.png"} url={"stockhub.app"} on:sub={handleSub} bind:maybe={subp} >
                <p slot="desc">
                StockHub is a free to use PWA that tracks daily tweets and Reddit posts for 8000 US securities, as well as options volume data
                for 530 stocks every 5 minutes. It helps track short term trends in the market and thus helps retail investors with more information.
                
                <br>
                  <br>
                I built it over the summer (2020), after I saw some bizzare market movements and was curious to find out more. One thing led to another and 
                I decided that building StockHub would be a great way to identify such behaviour and also help out all the retial investors I saw online
                who were trying to chase long term porfits with short term trends. It also runs NLP on each tweet and Reddit post to generate an average 
                sentiment score for every stock, based on social mentions from the previous day.
                <br>
                  <br>
                It is built using Svelte/Sapper for the frontend, and GCP serverless for backend (interact with private APIs). More info and a diagram <a href="https://stockhub.app/Data">here</a>.
                <br><br>
                Technologies used: Svelte, Sapper, GCP (Functions, Run, Scheduler, PubSub), Python, JavaScript, Node, Docker, Firebase (RTDB, Hosting, Analytics).
                <br><br>
                APIs used: Robinhood, YahooFinance, Twitter, and Reddit.
                            <br><br>
                </p>
                </Card>
                <Card name={"Portfolio"} img={"thisite.png"} url={"aparimeya.xyz"} on:sub={handleSub} bind:maybe={subp}>
                    <p slot="desc">
                        This is the cool space/tech themed portfolio you are looking at right now! 
                        <br><br>
                        Thanks to the magic of Svelte and as a personal challenge to myself, this website only has devDependencies :)
                        <br><br>
                        Technologies used: Svelte, JavaScript, Netlify.
                        <br><br>
                    </p>
                </Card>
                <Card name={"StudentSide"} img={"ssl.png"} url={"studentside.org"}  on:sub={handleSub} bind:maybe={subp}>
                    <p slot="desc">
                        This summer/start of fall, I was brought on as a freelancer to help integrate and finish up StudentSide's web platform. 
                        I worked with their exisiting team and built them APIs as needed. All of their infrastructure was
                        hosted on AWS, but to savet time and costs I deployed my serverless functions to GCP.
                        <br><br> 
                        I also helped them set up their hosting solution, by putting their static react site on Firebase hosting. 
                        <br><br>
                        Authentication is handled via JWT. This works perfectly for a modular serverless setup.
                        <br><br>
                        Technologies used: Python, GCP Functions, Firebase.
                        <br><br>
                    </p>
                </Card>
                <Card name={"Aether"} url={"aether-five.vercel.app"} on:sub={handleSub} bind:maybe={subp}>
                    <p slot="desc">
                        Aether is a cryptocurrency paper trading platform that also allows for social interaction on all transacitons.
        
                        <br><br> 
                        It is currently under developement and is the final group project for one of my classes. Normally I would not put a class
                        project here but this class gave us full autonomy as to the tech stack we can use as well as what we can make. Stay tuned for updates!
                        
                        <br><br>
                        Technologies used: Svelte, Sapper, Python, GCP Functions, Firebase (Firestore, RTDB), Vercel.
                        <br><br>
                    </p>
                    </Card>

                <Card name={"ESSI"}  img={"nv.png"} url={"Classified Deployment"} on:sub={handleSub} bind:maybe={subp} >
                        <p slot="desc">
                        Worked on a realtime vehicle tracking platform as part of my internship. While my work was focused on remaking the broken and outdated 
                        UI, I also got to collaborate with senior devs and help with a Node.JS as well as a MySQL server. 
                        <br><br> 
                        Technologies used: Vue, JavaScript, Node, MySQL.
                        <br><br>
                    </p>
                    </Card>
                <Card name={"Humblef00ls"} img={"hf.png"} url={"instagram.com/humblef00ls"}  on:sub={handleSub} bind:maybe={subp}>
                    <p slot="desc">
                       Since 2017 I have been creating digital art. It stared off as a hobby but soon became very relevant to 
                       all my school projects, as is ultimately what got me into web dev. 
                        <br><br> 
                        I make art and do freelance graphic design work, mostly logos, and have had my art featured at the Rubenstien Center For Arts at Duke
                        University.
                        <br><br> 
                        Technologies used: Photoshop, Illustrator.
                        <br><br>
                    </p>
                </Card>
                <Card name={"DIDA"} url={"sites.duke.edu/dida"} on:sub={handleSub} bind:maybe={subp} >
                                    <p slot="desc">
                      I work part time at the Duke Innovate Design Agency, a student staffed creative services organisation.
                        <br><br> 
                      Since starting in 2018 I have had many great opportunities and gotten to work with a lot of diffrenent organisations on campus,
                      mostly student orgs but also Duke Admin and even Duke Chappel once.
                        <br><br> 
                        Technologies used: Photoshop, Illustrator.
                        <br><br>
                    </p>
                </Card>
                <Card name={"Duke Gaming"} img={"dg.png"} url={"facebook.com/dukeugaming"} on:sub={handleSub} bind:maybe={subp} >
                        <p slot="desc">
                      I helped co-found Duke Gaming, Duke's first gaming and esports club. Since then I have been head of marketing and design.
                        <br><br> 
                      The community has slowly grown since we started, and now when everyone is home we all are more connected than ever.
                      While we mostly host tournaments, we also collaborated with Duke Rec to host VR events. Currently I am in the middle of
                      setting up a Minecraft Server on AWS for the Duke Community due to popular demand. 
                        <br><br> 
                        Technologies used: AWS Lightsail, Illustrator, Photoshop, Linux.
                        <br><br>
                    </p>
                </Card>

        </article>
        <Nav />
    </div>


<style>
    .close{
        right:0px;

    }
    .c2{
        right:65px;
    }
    .panel{
        top: 3vh;
        height: 97vh;
        min-width: 300px;
        left:3vw;
        width: 94vw;
        border-radius: 15px 15px 0px 0px;
    }

    h2{
        padding-left: calc(1vw + 10px);
        flex-direction: row;
    }



    a{
        text-decoration: underline
    }
    article{
        display: flex;
    justify-content: space-evenly;
    flex-wrap: wrap
    }
 p{
         padding:0px;
    margin-left:20px;
    margin-right:20px;
    font-size: 1.5em;
 }
</style>