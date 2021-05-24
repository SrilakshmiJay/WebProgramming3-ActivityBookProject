<svelte:head>
      <link rel="stylesheet" href="../../build/style1.css">
</svelte:head>

<script>
    let questions = [
		{ id: 1, text: 'The blanket kept them warm.', answer: 'blanket', token:'b'},
		{ id: 2, text: 'There were ants on the picnic table.', answer: 'ants', token:'a' },
		{ id: 3, text: 'She turned the light on in the kitchen', answer: 'light', token:'l' },
                { id: 4, text: 'They drew a straight line.', answer: 'line', token:'l' },
                { id: 5, text: 'She swam right past the Octopus.', answer: 'octopus', token:'o' },
                { id: 6, text: 'An octagon has eight sides.', answer: 'octagon', token:'o' },
                { id: 7, text: "He can't pronounce her name.", answer: 'name', token:'n' }
    ];

    let selected;
    let chosen = '';

    let displayState = '_'.repeat(questions.length);
    let currentState = displayState.split('');
    let src ='';
    let src_alt = '';

   
    function handleSubmit(chosen) {
        for(let i = 0; i < questions.length; i++){
            if (questions[i].answer === chosen) {
                currentState[i] = questions[i].token;

                displayState = currentState.join('');

                src = '../../../build/images/greatjob.png';
                src_alt ="balloon image";
            } 
            if (selected.answer !== chosen) {
                src = '../../../build/images/tryagain1.png' ;  
                src_alt ="try again image";
            }          
        }

    }

    
</script>

<style>
h1{
        color:#401115 ; 
} 
h4{
        color:#AA2123
}
#noun{
        font-family: 'Akaya Kanadaka';
        background-color: #928989;
}
input { 
        display: block;
        width: 300px; 
        margin-top: 80px;
        max-width: 100%;
        margin-left: 320px;
      
}
input, select, button{
        background-color: rgb(190, 194, 185) ;
        border-radius: 0.2em;
}

#animeshake{
        margin-left: 940px;
}

#animeshake {
        animation: shake 0.8s;
        animation-iteration-count: infinite;
}
    
@keyframes shake {
        0% { transform: translate(1px, 1px) rotate(0deg); }
        10% { transform: translate(-1px, -2px) rotate(-1deg); }
        20% { transform: translate(-3px, 0px) rotate(1deg); }
        30% { transform: translate(3px, 2px) rotate(0deg); }
        40% { transform: translate(1px, -1px) rotate(1deg); }
        50% { transform: translate(-1px, 2px) rotate(-1deg); }
        60% { transform: translate(-3px, 1px) rotate(0deg); } 
        70% { transform: translate(3px, 1px) rotate(-1deg); }
        80% { transform: translate(-1px, -1px) rotate(1deg); }
        90% { transform: translate(1px, 2px) rotate(0deg); } 
        100% { transform: translate(1px, -2px) rotate(-1deg); }
}

#balloon1,#balloon{
         position: relative;
         margin-right: 1400px;
}
#balloon1{
        animation: fly 15s ;
}
@keyframes fly {
        from {bottom: 400px;}
        to {bottom:1200px;}
}

span {
		display: inline-block;
		padding: 0.1em 0.1em;
		margin: 0 0.2em 0.6em 0;
		width: 1.6em;
		text-align: center;
		border-radius: 0.2em;
	    background-color: rgb(190, 194, 185);
        font-size: 60px;
        font-weight: bold;
        color:#401115 ;
}

</style>

<div class="card">
<div id ="noun">
<h1>Get this Noun off the Ground</h1>
<h4>Select the first noun in each sentence, not including pronouns.<br>
     The first letter of the noun will be auto filled <br>
      to decode the message.</h4>
           
    <div id ="animeshake">
        <img {src} alt ={src_alt}>
    </div>
    
<form on:submit|preventDefault={handleSubmit(chosen)} >
	<select bind:value={selected} >
		
        {#each questions as question}
			<option value={question}>
				{question.text}
            </option>
          
        {/each}
	</select>
  
    
    <h4>Selected question {selected ? selected.id : '[waiting...]'}</h4>
  
    <input bind:value={chosen} on:focus="{() => chosen = ''}" on:focus="{() => src = ''}" on:focus="{() => src_alt = ''}"  >
    
    <button disabled={!chosen} type=submit  >
		Submit
       
	</button>
   
</form>

{#each displayState as letter}
	
		<span>{letter}</span>
    
{/each}

</div>
</div>

{#if displayState != 'balloon'}
<div id="balloon" ><img src="../../../build/images/balloon1.png"  alt ="Man in Parachute"> </div>
{:else if displayState === 'balloon'}
<div id="balloon1" ><img src="../../../build/images/balloon1.png" alt ="Man in Parachute"> </div>
{/if}

 
