<script lang="ts">
  import logo from './assets/svelte.svg'
  import '@fortawesome/fontawesome-free/css/all.min.css'
  import Header from './lib/Header.svelte';
  import Share from './lib/Share.svelte';
  import CategoryFood from './lib/CategoryFood.svelte';

  let title:string = "Hop Supply";
  interface Product {
    title: string;
    desc: string;
    image: string;
    quantity: Array<{ amount: number, price: number }>
  }
  let products: Product[] = [
    { "title": "Picada Clasica", "desc": "Jamon cocido", "image": "https://placehold.co/450x300", "quantity": [{"amount": 2, "price":15000}] },
    { "title": "Picada Extrema", "desc": "Jamon cocido con queso", "image": "https://placehold.co/450x300", "quantity": [{"amount": 1, "price":15000},{"amount": 2, "price":17500},{"amount": 3, "price":20000}] },
    { "title": "Picada Nueva", "desc": "Jamon cocido con queso, tomate y multiples carnes", "image": "https://placehold.co/450x300", "quantity": [{"amount": 1, "price":10000}] },
  ];
  let categories: { title: string, desc: string, featured: string, products: Product[] }[] = [
    { "title": "Picadas", "desc": "Picadas de carne", "featured": "featured", "products": products },
    { "title": "Milanesas", "desc": "", "featured": "", "products": products },
    { "title": "Pizzas", "desc": "Estilo napolitano", "featured": "", "products": products },
  ]

  
</script>
<main>
  <Header {title} {logo} />
  
  <div>
    <div class="banner">
      <img src="https://placehold.co/1920x1080" alt="Hop Supply banner" />
    </div>
    <Share />
    <CategoryFood {categories} />
  </div>
  
</main>

<style>
  .banner{
    width: 100%;
    height: 300px;
    display: flex;
  }
  .banner img{
    width: 100%;
    object-fit: cover;
    display: flex;
  }
</style>
