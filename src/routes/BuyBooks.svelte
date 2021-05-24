

<svelte:head>
      <link rel="stylesheet" href="../../build/style1.css">
</svelte:head>
<script>

let cart = [];
let products = [{id:1, name: "Peacock", image:"../../build/images/Book20.jpg", price: 12,quantity:1},
                {id:2, name: "Rhyming Riddles", image:"../../build/images/Book21.jpg", price: 10,quantity:1},
                {id:3, name: "Book of Numbers", image:"../../build/images/Book22.jpg", price: 6,quantity:1},
                {id:4, name: "The Day you Begin", image:"../../build/images/Book23.jpg", price: 8,quantity:1},
                {id:5, name: "We beat you because we love you", image:"../../build/images/Book24.jpg", price: 6,quantity:1},
                {id:6, name: "Why is FEMINISM so silly", image:"../../build/images/Book25.jpg", price: 10,quantity:1},
                {id:7, name: "Chicka chicka Boom Boom", image:"../../build/images/Book26.jpg", price: 13,quantity:1},
                {id:8, name: "We help Daddy Hide the Body", image:"../../build/images/Book27.jpg", price: 6,quantity:1},
                {id:9, name: "Charlotte's web", image:"../../build/images/Book28.jpeg", price: 10,quantity:1},
                {id:10, name: "Beautiful Bird Books for Kids", image:"../../build/images/Book29.jpg", price: 15,quantity:1},
                {id:11, name: "Noun", image:"../../build/images/Book30.jpg", price: 6,quantity:1},
                
]

const addToCart = (product)=> {
    for (let item of cart){
        if(item.id === product.id){
            product.quantity += 1
            cart = cart;
            return;
        }
    }
    cart = [...cart, product]
}

const minusItem = (product)=> {
    for (let item of cart){
        if(item.id === product.id){
            product.quantity -= 1
            cart = cart;
            return;
        }
    }
    cart = [...cart, product]
}

const plusItem = (product)=> {
    for (let item of cart){
        if(item.id === product.id){
            product.quantity += 1
            cart = cart;
            return;
        }
    }
    cart = [...cart, product]
}

$: total = cart.reduce((sum,item) => sum + item.price * item.quantity, 0)



</script>
<style>
button{
        background-color: rgb(190, 194, 185) ;
        border-radius: 0.2em;
}
.product-list, .cart-item{
        display: grid;
        grid-template-columns: repeat(2, 1fr);
       
}

.image{
        height:90px;
        width:70px;
        background-size: contain;
        background-position:center;
        background-repeat: no-repeat;
}

.total{
        text-align: right;
}

.cart-list{
        border: 2px solid;
        padding: 10px;
        
}
.card{
        background-color: rgb(219, 215, 215);
}

</style>
<div class="card">

<p>There are {cart.length} items in your cart</p>
<div class = "product-list">
    {#each products as product}
        <div>
            <div class= "image" style = "background-image:
             url({product.image}"></div>
             <h6>{product.name}</h6>
             <h6>$ {product.price}</h6>
             <button on:click = {()=> addToCart(product)}>
                Add To Cart</button> <hr> <hr>  
            </div>
    {/each}
</div>


<div class ="cart-list">
    {#each cart as item}
    {#if item.quantity > 0}
    <div class = "cart-item">
        <img width = "50" src={item.image} alt= {item.name}/>
        <div>
            {item.quantity}
            <button on:click={()=> minusItem(item)}>-</button>
            <button on:click={()=> plusItem(item)}>+</button>
        </div>
        <p>${item.price * item.quantity}</p> 
    </div>
    <hr> 
    {/if}
    
    {/each}

    <div class = "total">
        <h4>Total: $ {total}</h4>
    </div>
</div>
</div>
