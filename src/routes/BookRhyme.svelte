<svelte:head>
      <link rel="stylesheet" href="../../build/style1.css">
</svelte:head>

<script>
    	import { fade, fly,  } from 'svelte/transition';
        let show = true;
        let chosen = '';
        let selected;
        let imgans;
        let src ='';
        let src_alt = '';
       
        let questions = [
		{ id: 1, image: "../../../build/images/monkey.jpg", tryagain: "../../../build/images/tryagain1.png", display: false, text: "Look at me! I'm up a tree! As every primate wants to be. I'm upside -down, just hanging 'round. will you climb this vine with me? What am I?' ", answer: 'monkey'},
		{ id: 2, image: "../../../build/images/snake1.jpeg", tryagain: "../../../build/images/tryagain1.png",  display: false, text: "Look at me! I'm in the grass. Another word for me is asp. I'm slithering. Not dithering. if you see me, you might gasp. What am I?", answer: 'snake'},
		{ id: 3, image: "../../../build/images/elephant.jpg", tryagain: "../../../build/images/tryagain1.png",  display: false, text: "Look at me! I'm big and round. We pachyderms sure pound the ground. I like to stomp. I like to romp. With my trunk I make cool sounds. What am I?", answer: 'elephant'},
        { id: 4, image: "../../../build/images/austin.jpeg", tryagain: "../../../build/images/tryagain1.png",  display: false, text: "Look at him! He's a truly amazing professor at DCTC! Hard to find and impossible to forget! He is so kind, patient and helpful! Who is he?", answer: 'austin'},
	    ];

    function handleSubmit() {
       
        for(let i = 0; i < questions.length; i++){
           
            if (selected.answer === chosen) {
              questions.display = true;
            }
            if (selected.answer !== chosen) {
                src = '../../../build/images/tryagain1.png' ;  
                src_alt ="try again image";
            }

      
        }

    }

</script>

<style>
.box{
        display: grid;
        place-items:center;
        width: 400px;
        height:260px;
        background-color: khaki;
        border-style:inset;
        border-width: 6px;
        border-color:#e2dae7;
        border-radius: 10px;
        margin-left: 258px;
}

.image{
        height:200px;
        width:200px;
        border-radius: 100%;
        background-size: contain;
        background-position:center;
        background-repeat: no-repeat;
    }
.card{
        background-color: rgb(196, 199, 178);
        font-family: 'New Tegomin';
        color:#1e0f27;
}
.background{
        height:290px;
        width:943px;
        background-color: rgb(157, 177, 162);
        opacity: 99%;
}
h1{
        color:#2d1c38 ; 
} 
h4{
        color:#884b1a
}
input { 
        width: 300px; 
        margin-top: 80px;
        max-width: 100%;
        background-color: rgb(230, 187, 109) ;
        border-style:inset;
        border-width: 6px;
        border-color:#e2dae7;
        opacity: 80%;
        border-radius: 10px;

}
textarea{
        width: 800px; 
        height: 160px;
        background-color: khaki ;
        border-style:inset;
        border-width: 6px;
        border-color:#e2dae7;
        border-radius: 10px;
        opacity: 99%;
    

}
select, button{
        background-color: rgb(230, 187, 109) ;
        border-style:inset;
        border-width: 6px;
        border-color:#e2dae7;
        opacity: 99%;
        border-radius: 10px;
}
</style>

<div class="card">

    <h1>Rhyming Riddles</h1>
    <h4>Sometimes big words are used for well -known words. 
        See if you can tell what the words in bold are by 
        reading the clues in the poem. Then click to see the image.</h4>

    <form on:submit|preventDefault={handleSubmit}>
        <div class="background">
            <select bind:value={selected} on:focus="{() => chosen = ''}" on:focus="{() => questions.display = false}"   >
            
                {#each questions as question}

                <option value={question}>
                    Riddle {question.id}
                </option>
                {/each}
                
            </select>
            <textarea>{selected ? selected.text : '[waiting...]'}</textarea>
        </div>
        <input bind:value={chosen} on:focus="{() => chosen = ''}" on:focus="{() => src = ''}" on:focus="{() => src_alt = ''}" on:focus="{() => questions.display = false}"  >
        <button disabled={!chosen} type=submit >
        Submit
        </button>
    </form>
    <img {src} alt ={src_alt}>

    {#if show}
        <div class ="box"  transition:fade={{duration: 5000}}>

            {#if questions.display}
                <div class ="image" transition:fly|local={{x: 500}} style = "background-image:
                url({selected.image} ">
                </div>
            {/if}

        </div>
    {/if}

    <input type=checkbox bind:checked={questions.display}>
    Click to see the answer

</div> 


