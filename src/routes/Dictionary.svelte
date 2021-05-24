<script>
   
import { Router, Link, Route } from 'svelte-routing';

   
    let findWord = "";
    let audioCode ="";
    let subDir = "";

    async function getDef(findWord) {
       console.log(findWord);
       const response = await fetch('https://www.dictionaryapi.com/api/v3/references/collegiate/json/' + findWord + '?key=ede93754-5019-4a60-a008-cefa8b43327a');
       const data = await response.json();

        audioCode = data[0].hwi.prs[0].sound.audio
       
        var numberPattern = new RegExp("[0-9]");
        var symbolPattern = new RegExp("[^0-9a-zA-Z]");
        
        if(audioCode.startsWith("bix")){
            subDir = "bix";
        }
        else if(audioCode.startsWith("gg")){
            subDir = "gg";
        }
        else if(numberPattern.test(audioCode.charAt(0)) || symbolPattern.test(audioCode.charAt(0))) {       
            subDir = "number";
        }
        else {
            subDir =(audioCode.substr(0,1))
        }
    
        console.log('sub Directory value', subDir);
        return data;
    }

</script>

<style>
.card {
    min-height: 600px;
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
    transition: 0.3s;
    display: block;
    margin-left: auto;
    margin-right: auto;
    width: 60%;
    background-color: #928989;
    color:rgb(83, 82, 83);
    border-radius: 0.4em;
   
}
input{
    background-color: rgb(190, 194, 185) ;
    border-radius: 0.2em;
    margin-top: 40px;
}

ul li{
   font-weight:normal;
   list-style: none;
} 
h1{
   color:rgb(112, 59, 59);    
}
h3{
   color:rgb(146, 75, 75);
}

</style>
<div class="card">

<input bind:value={findWord} on:focus="{() => findWord = ''}"  placeholder="Enter Word" >

{#await (getDef(findWord))}
    loading
    {:then dictionarydata}  
  
    <h1>Definition of {findWord}</h1>
    <h5>Click play button for <img src="../../../build/images/audio.png"
        alt="tshirt with custom text"
        ></h5>
    <!-- <a target="_blank" href="https://media.merriam-webster.com/audio/prons/en/us/mp3/{subDir}/{audioCode}.mp3">
        <img src="../../../build/images/audio.png"
        alt="tshirt with custom text"
        ></a>  -->
    
    <!-- svelte-ignore a11y-media-has-caption -->
    <audio controls>
        <source src="https://media.merriam-webster.com/audio/prons/en/us/mp3/{subDir}/{audioCode}.mp3" type="audio/mpeg">
    </audio>
    
   <ul>   
    {#each dictionarydata as dicdata} 
        <h3>{dicdata.fl}</h3>

        {#each dicdata.shortdef as data}
        <li>
        {data}<br><br>
        </li>
        {/each}
    {/each}

   </ul>
{/await}
</div>
