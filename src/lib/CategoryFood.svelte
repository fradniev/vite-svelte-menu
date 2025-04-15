<script lang="ts">
    interface Product {
        title: string;
        desc: string;
        image: string;
        quantity: Array<{ amount: number, price: number }>
    }
    let {
        categories = null,
    }:{
        categories?: { title: string, desc: string, featured: string, products: Product[] }[] | null; 
    }  = $props();
    function collapse(index:number):void {
        let newactive = document.getElementById('category-' + index);
        // Only allows one active category to be open at a time
        let element = document.getElementsByClassName("active");
        if(element.length > 0){
            if(element[0] !== newactive) {
                element[0].classList.remove('active');
                newactive.classList.toggle('active');
                return;
            } 
        }

        newactive.classList.toggle('active');
    }
</script>
<div class="category-food">
    <div class="food-card">
        {#each categories as category,index}
        <div id="category-{index}" class="food-category-collapse {category.featured}">
            <button onclick="{() => collapse(index)}" class="food-category-name">
                <div class="category-info">
                    <h3>{category.title}</h3>
                    <p>{category.desc}</p>
                </div>
                <i class="fa-solid fa-angle-up"></i>
            </button>
            {#each category.products as product}
            <div class="food-item">
                <div class="food-left">
                    <div class="food-title"><h4>{product.title}</h4></div>
                    <div class="food-desc"><i>{product.desc}</i></div>
                    <div class="food-amount">
                        {#each product.quantity as quantity, productIndex}
                        Para <span class="food-amount">{quantity.amount}</span> <span class="food-price">$ {quantity.price}</span> {#if product.quantity.length > productIndex+1}/&nbsp;{/if} 
                        {/each}
                    </div>
                    <div class="food-button">
                        <button>Pedir <i class="fa-solid fa-plus"></i></button>
                    </div>
                </div>
                <div class="food-right">
                    <div class="food-image">
                        <img src="{product.image}" alt="Hop Supply food" />
                    </div>
                </div>
            </div>
            {/each}
        </div>
        {/each}
    </div>
</div>

<style>
    .category-food{
        width: 100%;
    }
    .food-card{
        width: 100%;
    }
    .food-category-collapse{
        width: 100%;
        color:black;
    }
    .food-category-name{
        width: calc(100% - 2px);
        display: flex;
        align-items: center;
        justify-content: center;
        box-shadow: 0px 5px 5px #0a0a0a80;
        cursor:pointer;
        text-transform: uppercase;
        border-radius: 0;
        background-color: transparent;
        color: black;
        border: unset !important;
        outline:unset !important;
    }
    .food-category-name .category-info{
        width: 95%;
    }
    .food-category-name i{
        justify-self: flex-end;
        font-size: 1.5rem;
        margin-right: 15px;
        transform: rotate(180deg);
        transition: all .2s;
    }
    :global(.food-category-collapse.active i){
        transform: rotate(0deg);
    }
    :global(.food-item){
        width: 100%;
        height: 0;
        min-height: 0;
        overflow: auto;
        display: flex;
        justify-self: space-around;
        align-items: center;
        border-bottom: 0px solid black;
        transition: all .6s;
    }
    .food-left{
        display: flex;
        flex-direction: column;
        width: 63%;
        text-align: left;
    }
    .food-left .food-title h4{
        font-size: 1.2rem;
        margin: 0;
    }
    .food-price{
        color: #676767;
    }
    .food-left div{
        padding-left: 10px;
    }
    .food-right{
        display: flex;
        width: 35%;
    }
    .food-right img{
        width: 100%;
        object-fit: contain;
    }
    :global(.food-category-collapse.active .food-item){
        min-height: 200px;
        height: auto;
        border-bottom: 1px solid black;
    }
    .food-button button{
        color:black;
        background: #f29f12;
    }
    .featured{
        background: #ffe9007d;
    }
</style>