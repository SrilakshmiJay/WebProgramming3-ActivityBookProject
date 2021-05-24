<script>
    import { Capacitor } from '@capacitor/core';
	const platform = Capacitor.getPlatform();
	import { Router, Link, Route } from 'svelte-routing';
	
	import Home from './routes/Home.svelte';
	import LearnAboutPeacock from './routes/LearnAboutPeacock.svelte';
	import BookRhyme from './routes/BookRhyme.svelte';
	import BookNumbers from './routes/BookNumbers.svelte';
	import BookList from './routes/BookList.svelte';
	import Peacock1 from './routes/Peacock1.svelte';
	import Peacock2 from './routes/Peacock2.svelte';
	import Peacock3 from './routes/Peacock3.svelte';
	import Peacock4 from './routes/Peacock4.svelte';
    import Dictionary from './routes/Dictionary.svelte';
	import Noun from './routes/Noun.svelte';
	import BuyBooks from './routes/BuyBooks.svelte';
	

	export let url = "";
</script>

<style>
	
    @import url('https://fonts.googleapis.com/css2?family=Reggae+One&display=swap');
    @import url('https://fonts.googleapis.com/css2?family=Kurale&family=Redressed&display=swap');
	@import url('https://fonts.googleapis.com/css2?family=Redressed&display=swap');
    @import url('https://fonts.googleapis.com/css2?family=Akaya+Kanadaka&display=swap');
	@import url('https://fonts.googleapis.com/css2?family=Caveat:wght@500&family=New+Tegomin&family=Satisfy&display=swap');
	/* 'Akaya Telivigala','Potta One','Akaya Kanadaka' 'Hachi+Maru+Pop'*/
div{
    padding:0;
    margin:0;
    font-family:Reggae One;
    background-color:rgb(157, 177, 162);
    color:rgb(50, 78, 66);
	text-align:center;
	font-size: 25px;
}

h1{
	font-size: 50px;
	background-color:#646262;
	color:rgb(46, 61, 55);
    width:100%;	
	height:70px ;
	text-shadow: 2px 2px 5px rgb(233, 85, 97);
}
h4{
    color:#DB4332;
	background-color:#646262;
	height:40px ;
	text-shadow: 2px 2px 5px rgb(110, 34, 59);
}
div.sticky {
      position: -webkit-sticky;
      position: sticky;
      top: 0px;
	  width: 100%;
	  justify-content: space-evenly;
	  text-decoration: none;
	 
}
button{
	background-color:rgb(233, 114, 85);
	text-shadow: 2px 2px 5px rgb(110, 34, 59);
	color:#646262;
    border-radius: 20px;
    border-width:3px;
    border-color: #646262;
    height:54px;
    width: 200px;
    margin-left: 200px;
} 

</style>

<div>
	<Router url="{url}">
		
		<div class="sticky">
			<h1>Brain Power Books</h1>
		    <Link to="/"><img src="../../build/images/Home2.png"
			alt="Home"></Link>
			<button><Link to="/BookList">Read Books</Link></button>
			<button><Link to="/Dictionary">Dictionary</Link></button>
			<button><Link to="/BuyBooks">Buy Books</Link></button>
		
			<h4>The World belongs to those who Read!</h4>
			
		</div>
		<Route path="BuyBooks/">
			<BuyBooks/>
		</Route>

		<Route path="Noun/">
			<Noun/>
		</Route>

		<Route path="Dictionary/">
			<Dictionary/>
		</Route>

		<Route path="Peacock4/">
			<Peacock4 />
		</Route>

		<Route path="Peacock3/">
			<Peacock3 />
		</Route>

		<Route path="Peacock2/">
			<Peacock2 />
		</Route>

		<Route path="Peacock1/">
			<Peacock1 />
		</Route>

		<Route path="BookList/">
			<BookList />
		</Route>

        <Route path="BookNumbers/">
			<BookNumbers />
		</Route>
		
		<Route path="BookRhyme/">
			<BookRhyme />
		</Route>
		
		<Route path="learnaboutpeacock/">
			<LearnAboutPeacock />
		</Route>
		
		<Route path="/">
			<Home />
		</Route>
	
	</Router>
</div>