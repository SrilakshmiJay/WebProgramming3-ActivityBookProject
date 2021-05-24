<script>
    import { Router, Link, Route } from 'svelte-routing';
</script>
<style>
nav{
        width:100%;
        padding-bottom: 120px;
        text-shadow: 2px 2px 5px rgb(110, 34, 59);
        font-size: 40px;
        text-align:center;
        align-items: center;
        justify-content:space-around;
        list-style: none;
} 
ul li{
        padding: 60px 60px;
        font-weight:bold;
        color:rgb(69, 119, 98);
        text-align: center;
        display: inline-block;
}
li:active{
        background:rgb(198, 206, 209);
}
</style>
<h2>CHILDREN'S BOOKS (AGE 5-11)</h2>
<img src="../../build/images/star.png"
        alt="star"
        >

<nav>
	<ul>
			
    <li><Link to="/learnaboutpeacock"><img src="../../build/images/Book20.jpg"
                alt="Book20"
                ></Link></li>

    <li><Link to="/BookRhyme"><img src="../../build/images/Book21.jpg"
                alt="Book21"
                ></Link></li>

    <li><Link to="/BookNumbers"><img src="../../build/images/Book22.jpg"
                alt="Book22"
                ></Link></li>

    <li><Link to="/"><img src="../../build/images/Book23.jpg"
                alt="Book23"
                ></Link></li>

    <li><Link to="/booknumbers"><img src="../../build/images/Book24.jpg"
                alt="Book24"
                ></Link></li>

    <li><Link to="/booknumbers"><img src="../../build/images/Book25.jpg"
                alt="Book25"
                ></Link></li>

    <li><Link to="/booknumbers"><img src="../../build/images/Book26.jpg"
                alt="Book26"
                ></Link></li>

    <li><Link to="/booknumbers"><img src="../../build/images/Book27.jpg"
                alt="Book27"
                ></Link></li>

    <li><Link to="/booknumbers"><img src="../../build/images/Book28.jpeg"
                alt="Book28"
                ></Link></li>

    <li><Link to="/booknumbers"><img src="../../build/images/Book29.jpg"
                alt="Book29"
                ></Link></li>

    <li><Link to="/Noun"><img src="../../build/images/Book30.jpg"
                alt="Book23"
                ></Link></li>

    </ul>
</nav>