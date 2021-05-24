<script>
    import { Router, Link, Route } from 'svelte-routing';
</script>

<svelte:head>
      <link rel="stylesheet" href="../../build/style1.css">
</svelte:head>
<style>
    /* img.sticky {
      position: -webkit-sticky;
      position: sticky;
      top: 0;
      width: 200px;
    } */
    .zoom:hover {
  transform: scale(1.5); /* (150% zoom - Note: if the zoom is too large, it will go outside of the viewport) */
}
    </style>
<div class="card">
    
  <img class="zoom" src="../../../build/images/peacock-parts.jpg"
  alt="peacock-parts"
  >

</div>
<div class="container">
    <div class="arrow">
    <Link to="/Peacock2"><img src="../../build/images/leftarrow.png"
        alt="leftarrow"
        ></Link>
        <Link to="/Peacock4"><img src="../../build/images/rightarrow.png"
        alt="rightarrow"
        ></Link>
        </div>
</div>

