<template>
    <div id="nav">
        <nav>
            <router-link to="/" id="logo-url">
                <img id="logo" :src="logo" :alt="alt">
            </router-link>
            <router-link class="nav-link" to="/">Home</router-link> |
            <router-link class="nav-link" to="/pedido">Pedidos</router-link>
        </nav>

    </div>
</template>

<script>

    export default{
        name: 'Navbar',

        props: ['logo', 'alt']
    }

</script>

<style scoped>
    nav{
        padding: 18px 10px;
        background: #333;
        color: #fff;
        display: flex;
        gap: 6px;
        justify-content: flex-end;
        align-items: center;
    }

    #logo-url{
        margin: auto;
        margin-left: 0;
    }

    #logo{
        max-width: 40px;
    }

    nav .nav-link{
        color: #fcba03;
        text-decoration: none;
        font-size: 1.2rem;
        transition: .5s;
    }

    nav .nav-link:hover{
        color: #fff;
    }

</style>