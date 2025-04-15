<script lang="ts">
    let { 
        title,
        logo 
    }:{
        title: string;
        logo: string;
    } = $props();
</script>

<nav class="header">
    <div class="nav-left">
        <div class="logo">
            <img src={logo} class="logo" alt="Hopp Supply Logo" />
        </div>
        <div class="title">{title}</div>
    </div>
    <div class="nav-right">
        <div class="nav-menu">
            <i class="fa-solid fa-bars"></i>    
        </div>
    </div>
</nav>

<style>
    .header{
        display: flex;
        position: fixed;
        background-color: white;
        top:0;
        left:0;
        width: 100%;
        color:black;
        align-items: center;
        justify-content: space-between;
        
    }
    .nav-left, .nav-right{
        display: flex;
        align-items: center;
        padding: 1rem;
    }
    .nav-right{
        display: flex;
        align-items: center;
    }
    .nav-menu{
        color:black;
        cursor: pointer;
    }
    .logo {
      height: auto;
      margin-right: 10px;
    }
</style>