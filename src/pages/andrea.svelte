<script>
    import { fly } from 'svelte/transition'
	import Heading from './compo/Heading.svelte'
    import Blossom from './compo/art/Blossom.svelte'
    import CharmingButton from './compo/art/CharmingButton.svelte'

    // Detect mobile
    let isMobile = /(android|bb\d+|meego).+mobile|avantgo|bada\/|blackberry|blazer|compal|elaine|fennec|hiptop|iemobile|ip(hone|od)|ipad|iris|kindle|Android|Silk|lge |maemo|midp|mmp|netfront|opera m(ob|in)i|palm( os)?|phone|p(ixi|re)\/|plucker|pocket|psp|series(4|6)0|symbian|treo|up\.(browser|link)|vodafone|wap|windows (ce|phone)|xda|xiino/i.test(navigator.userAgent) ||
    /1207|6310|6590|3gso|4thp|50[1-6]i|770s|802s|a wa|abac|ac(er|oo|s\-)|ai(ko|rn)|al(av|ca|co)|amoi|an(ex|ny|yw)|aptu|ar(ch|go)|as(te|us)|attw|au(di|\-m|r |s )|avan|be(ck|ll|nq)|bi(lb|rd)|bl(ac|az)|br(e|v)w|bumb|bw\-(n|u)|c55\/|capi|ccwa|cdm\-|cell|chtm|cldc|cmd\-|co(mp|nd)|craw|da(it|ll|ng)|dbte|dc\-s|devi|dica|dmob|do(c|p)o|ds(12|\-d)|el(49|ai)|em(l2|ul)|er(ic|k0)|esl8|ez([4-7]0|os|wa|ze)|fetc|fly(\-|_)|g1 u|g560|gene|gf\-5|g\-mo|go(\.w|od)|gr(ad|un)|haie|hcit|hd\-(m|p|t)|hei\-|hi(pt|ta)|hp( i|ip)|hs\-c|ht(c(\-| |_|a|g|p|s|t)|tp)|hu(aw|tc)|i\-(20|go|ma)|i230|iac( |\-|\/)|ibro|idea|ig01|ikom|im1k|inno|ipaq|iris|ja(t|v)a|jbro|jemu|jigs|kddi|keji|kgt( |\/)|klon|kpt |kwc\-|kyo(c|k)|le(no|xi)|lg( g|\/(k|l|u)|50|54|\-[a-w])|libw|lynx|m1\-w|m3ga|m50\/|ma(te|ui|xo)|mc(01|21|ca)|m\-cr|me(rc|ri)|mi(o8|oa|ts)|mmef|mo(01|02|bi|de|do|t(\-| |o|v)|zz)|mt(50|p1|v )|mwbp|mywa|n10[0-2]|n20[2-3]|n30(0|2)|n50(0|2|5)|n7(0(0|1)|10)|ne((c|m)\-|on|tf|wf|wg|wt)|nok(6|i)|nzph|o2im|op(ti|wv)|oran|owg1|p800|pan(a|d|t)|pdxg|pg(13|\-([1-8]|c))|phil|pire|pl(ay|uc)|pn\-2|po(ck|rt|se)|prox|psio|pt\-g|qa\-a|qc(07|12|21|32|60|\-[2-7]|i\-)|qtek|r380|r600|raks|rim9|ro(ve|zo)|s55\/|sa(ge|ma|mm|ms|ny|va)|sc(01|h\-|oo|p\-)|sdk\/|se(c(\-|0|1)|47|mc|nd|ri)|sgh\-|shar|sie(\-|m)|sk\-0|sl(45|id)|sm(al|ar|b3|it|t5)|so(ft|ny)|sp(01|h\-|v\-|v )|sy(01|mb)|t2(18|50)|t6(00|10|18)|ta(gt|lk)|tcl\-|tdg\-|tel(i|m)|tim\-|t\-mo|to(pl|sh)|ts(70|m\-|m3|m5)|tx\-9|up(\.b|g1|si)|utst|v400|v750|veri|vi(rg|te)|vk(40|5[0-3]|\-v)|vm40|voda|vulc|vx(52|53|60|61|70|80|81|83|85|98)|w3c(\-| )|webc|whit|wi(g |nc|nw)|wmlb|wonu|x700|yas\-|your|zeto|zte\-/i.test(navigator.userAgent.substr(0, 4))

    // Page transition
    let visible = false
    let id1 = setInterval(loadPage, 300)
    function loadPage() {
        visible = true
        clearInterval(id1)
    }

    // Content transition
    let visibleC = false
    let delay = 0
    let id2 = setInterval(loadContent, 500)
    function loadContent() {
        if(delay==1){
            visibleC = true
            clearInterval(id2)
        }
        else
            delay++
    }
</script>

<link href="https://fonts.googleapis.com/css2?family=La+Belle+Aurore&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Lancelot&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=PT+Sans:ital,wght@0,400;0,700;1,400;1,700&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Taviraj:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap" rel="stylesheet">

{#if visible}
<div class="about-ctr" in:fly="{{ x: -2000, duration: 800 }}" out:fly="{{ x: -200, duration: 800 }}">
    {#if !isMobile}
        <Heading title={"ABOUT"} />
    {/if}

    {#if visibleC}
        <div id="about-ctr-inner" transition:fly="{{y:100, duration: 800}}">
            <div id="photo-sect" class="sect">
                <div class="photo-ctr">
                    <div id="fleur1"><Blossom /></div>
                    <div id="fleur2"><Blossom color={"#CDFF9B"} height={"3em"} width={"3em"}/></div>
                    <div id="fleur3"><Blossom color={"#6CA6B8"}/></div>
                    <div class="frame">
                        <div id="photo"></div>
                    </div>
                </div>
            </div>
            <div id="info-sect" class="sect">
                <div class="info-box">
                    <div class="info-box-inner">
                        <div class="primary-text">
                            <div class="griddy-grid">
                                <div id="bigH" class="greeting">H</div>
                                <div class="greeting">ello! </div>
                                <div class="info-row griddy-text"> 
                                    My name is Andrea Abellera. I discovered my love for creation as a kid who created puzzles, board games, textbooks, stories, with a huge spiel of drawings.
                                </div>
                            </div>

                            <div class="info-row"> 
                                Discovering HTML and Flash-based virtual worlds sparked my desire to create things inside the computer. At 15, I graduated high school in the Philippines and moved with my family to Canada, allowing me to adapt culturally and gain exposure to animation, 3D models, different art media (clay, leather, textiles), programming, networks and cybersecurity. I took a year to go Bible College to pursue my love for God, Jesus Christ, to whom I attribute all things and has become my strength and buckler for years to come. I am currently studying Computer Science at the University of Manitoba hopeful to graduate on April 2023.
                            </div>

                            <div class="info-row logos">
                                <img src="https://ipfs.fleek.co/ipfs/bafybeibmpke7psgzgwmdo32imsyzryj3ep6l2oykjzkquhg5sq47ovp7ya" alt="University of Manitoba">
                            </div>
                            
                            <div class="info-row"> 
                                I document my development journey, programming studies, thoughts and adventures with <b> CasuallyDev </b> by night. By day, I work with TD Bank as a Business Systems Analyst Intern, which is a tremendously great experience!
                            </div>
                            
                            <div class="info-row logos">
                                <img src="https://ipfs.fleek.co/ipfs/bafybeib25qktipncncjuri6nkc55ftas3w4bshi7z3ijqz4he3iljg5mey" alt="Toronto-Dominion Bank">
                            </div>

                            <div class="info-row"> 
                                You can reach me best by sending a message on my 
                                <a href="https://www.linkedin.com/in/aabellera/"> LinkedIn </a>.  
                                I frequent <a href="https://www.instagram.com/ateawa/"> Instagram </a> but will only accept connections from people I know personally.
                            </div>
                        </div>
                        <div class="action-btns">
                            <a href="/intermission">
                                <CharmingButton text={"VIEW MY 🚲 PORTFOLIO"} />
                            <div id="resume" class="action-btn"> or <a href="https://ipfs.fleek.co/ipfs/bafybeih7ptrsrmnnceicfgdw73rq6shukib7owrsuz52wlrfrscqc57fzu"> Download my Résumé</a></div>
                        </div>
                        <div class="for-fun">
                            <div id="stamp-collection"></div>
                            <div id="drink-tier-list"></div>
                            <div id="stone-bridges"></div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    {/if}
</div>
{/if}

<style>
    .about-ctr {
        height: max-content;
        width: 100%;
        display: grid;
        grid-template-rows: auto 1fr;
        margin: -8vh 0 10vh 0;
    }

    #about-ctr-inner{
        display: grid;
        grid-template-columns: 50% 40%;
        position: relative;
    }

    .sect{
        display: grid;
        justify-items: center;
    }

    .photo-ctr{
        position: relative;
        width: 70%;
        height: 100%;
    }

    .info-box{
        height: max-content;
        width: 90%;
        color: var(--ink);
        background-color: var(--bark);
        box-shadow: 0.05em 0.15em 0.5em rgba(0,0,0,0.3);
        display: grid;
        justify-items: center;
        align-items: center;
        font-size: 1.1em;
        font-family: 'Taviraj', serif;
        margin-top: -3vh;
    }

    .info-box-inner{
        display:flex;
        flex-direction: column;
        height: auto;
        width: 80%;
        margin: 8vh 0 6vh 0;
        align-items: center;
    }

    #photo{
        background-image: url(https://ipfs.fleek.co/ipfs/bafybeifj2pisu4kore77t6krkqrd5yqqh2rrkbznfnksdnsmhd7eyqjvyu);
        background-size: cover;
        background-position: bottom;
        background-repeat: no-repeat;
        height: 93%;
        width: 90%;
    }

    #fleur1{
        position: absolute;
        z-index: 5;
        top: -2em;
        left: 20%;
    }

    #fleur2{
        position: absolute;
        z-index: 4;
        top: -2.75em;
        left: 30%;
    }

    #fleur3{
        position: absolute;
        z-index: 5;
        top: 30em;
        left: 65%;
    }

    .frame{
        position: absolute;
        z-index: 3;
        transform: translateX(-50%);
        left: 50%;
        display: grid;
        justify-items: center;
        align-items: center;
        width: 22em;
        height: 32em;
        background-color: var(--bark);
        box-shadow: 0.05em 0.15em 0.5em rgba(0,0,0,0.3);
    }

    #bigH{
        font-size: 7.5em;
        margin-top: -0.2em;
        grid-row: 1/3;
        grid-column: 1/2;
    }

    .greeting{
        font-family: 'Lancelot', cursive;
        font-size: 3em;
        margin-top: 1.5vh;
        color: var(--coffee);
    }

    .griddy-grid{
        display: grid;
        grid-template-columns: auto 1fr;
        grid-template-rows: auto auto;
    }

    .info-row{
        width: 100%;
        text-align: left;
        margin-bottom: 5vh;
    }

    .logos{
        display: flex;
        justify-content: center;
    }

    .logos img{
        height: 30%;
        width: 30%;
    }

    img:hover{
        animation: up 0.8s ease-out;
        cursor: url(https://ipfs.fleek.co/ipfs/bafybeicuryldiwjiv5qynwnswb6qxv2lujyxvcv3oodzrbegtq247jubvm), pointer;
    }

    .frame:hover{
        animation: upFrame 0.9s ease-out;
        cursor: url(https://ipfs.fleek.co/ipfs/bafybeicuryldiwjiv5qynwnswb6qxv2lujyxvcv3oodzrbegtq247jubvm), pointer;
    }

    .action-btns{
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
    }

    .action-btn{
        padding: 3vh 2vw 3vh 2vw;
        width: 100%;
    }

    /* #tour{
        border: 4px double var(--bark);
        background-color: var(--oyster);
    } */

    @keyframes up{
        0%{
            transform: translateY(0);
        }
        100%{
            transform: translateY(-0.6em);
        }
    }

    @keyframes upFrame{
        0%{
            transform: translate(-50%, 0);
        }
        40%{
            transform: translate(-50%, -0.6em);
        }
        100%{
            transform: translate(-50%, 0);
        }
    }

    @media screen and (max-width: 800px){
        #about-ctr-inner{
            grid-template-columns: 1fr;
            grid-template-rows: 88vh auto;
        }

        #bigH{
            font-size: 5.5em;
            grid-row: 1/2;
            grid-column: 1/2;
        }

        .griddy-text{
            grid-row: 2/3;
            grid-column: 1/3;
        }

        #info-sect{
            margin-top: 12vh;
        }

        .info-box{
            color: black;
            width: 100%;
            margin-top: -7vh;
        }

        .info-box-inner{
            width: 90%;
        }

        .info-row{
            margin-bottom: 8vh;
        }

        .logos img{
            height: 60%;
            width: 60%;
        }

        #fleur1{
            top: -2em;
            left: -15%;
        }

        #fleur2{
            position: absolute;
            z-index: 4;
            top: -2.75em;
            left: 15%;
        }

        #fleur3{
            position: absolute;
            z-index: 5;
            top: 30em;
            left: 87%;
        }
    }
</style>

